```C
#include "fractol.h"

void	my_mlx_pixel_put(t_img *img, int x, int y, int color)
{
// 이미지를 그릴 때, (x,y) 좌표에 원하는 색상을 넣음
// 이미지 메모리에서 (x,y) 좌표에 해당하는 위치를 계산한 후, 그 위치에 지정한 색상 값을 저장
	char	*dst;

	dst = img->addr + (y * img->line_length
			+ x * (img->bits_per_pixel / 8));
	*(unsigned int *)dst = color;
}

uint32_t	get_color(t_img img, int x, int y)
{
// 좌표에 이미 그려진 픽셀의 색상을 가져옴
// 좌표의 픽셀이 메모리에서 어디에 있는지 계산하고, 그 위치에 저장된 색상 값을 읽어옴
	return (*(uint32_t *)(img.addr
		+ (y * img.line_length + x * (img.bits_per_pixel / 8))));
}

```