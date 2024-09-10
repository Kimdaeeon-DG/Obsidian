```C
#include "fractol.h"

void	update_fractal_c(t_canvas *canvas)
{
	int		x;
	int		y;
	double	mouse_re;
	double	mouse_im;

	mlx_mouse_get_pos(canvas->mlx, canvas->win, &x, &y);
	// 현재 마우스의 (x, y) 좌표를 가져옴
	if (!x && !y) // 마우스 좌표가 (0, 0)일 경우 함수 종료
		return ;

	// 마우스의 x좌표를 실수 부분으로 변환
	mouse_re = (double)x
		/ (WIDTH / (canvas->max_re - canvas->min_re)) + canvas->min_re;
	// 마우스의 y좌표를 허수 부분으로 변환 (Y축은 위가 양수이므로 -1을 곱함)
	mouse_im = (double)y 
		/ (HEIGHT / (canvas->max_im - canvas->min_im)) * -1 + canvas->max_im;

	// 계산된 실수 및 허수 값을 프랙탈의 c 값으로 업데이트
	canvas->c_re = mouse_re;
	canvas->c_im = mouse_im;
}

int	main_loop(t_canvas *canvas)
{
	if (canvas->is_pressed_shift) // Shift 키가 눌렸을 때만 프랙탈 c값을 업데이트
		update_fractal_c(canvas);

	// 선택된 프랙탈 그리기 함수를 호출하여 화면에 프랙탈을 그림
	canvas->fractal_drawer(canvas);

	// 그려진 이미지를 창에 표시
	mlx_put_image_to_window(canvas->mlx, canvas->win, canvas->img.img, 0, 0);
	return (0);
}

bool	set_fractal_type(t_canvas *canvas, char *str)
{
	if (!ft_strncmp(str, "mandelbrot", 11))
		canvas->fractal_drawer = draw_mandelbrot;
	else if (!ft_strncmp(str, "julia", 6))
		canvas->fractal_drawer = draw_julia;
	else if (!ft_strncmp(str, "burningship", 12))
		canvas->fractal_drawer = draw_burningship;
	else
		return (false);
	return (true);
}

int	main(int argc, char **argv)
{
	t_canvas	canvas;

	if (argc != 2 || !set_fractal_type(&canvas, argv[1]))
	{
		printf("select\n"
			"- mandelbrot\n"
			"- julia\n"
			"- burningship\n");
		return (1);
	}
	initialize_canvas(&canvas); // 캔버스 초기화 (창, 이미지 등 설정)

	// 키 입력 관련 이벤트 처리
	mlx_hook(canvas.win, KeyPress, KeyPressMask, key_press_hook, &canvas);
	mlx_hook(canvas.win, KeyRelease, KeyReleaseMask, key_release_hook, &canvas);

	// 창 닫기 이벤트 처리
	mlx_hook(canvas.win, ClientMessage, 1L << 17, exit_canvas, &canvas);

	// 마우스 클릭 이벤트 처리
	mlx_mouse_hook(canvas.win, mouse_hook, &canvas);

	// 메인 루프에서 반복적으로 'main_loop' 호출
	mlx_loop_hook(canvas.mlx, &main_loop, &canvas);
	mlx_loop(canvas.mlx);
}

```