#include <stdio.h>
#include <stdbool.h>
#include "bsp.h"
#include "console.h"
#include "ls1c102.h"
#include "user_gpio.h"
#include "wdg.h"
extern HW_PMU_t *g_pmu;
int main(void)
{
    WdgInit();
    gpio_init(39,0);//投影灯信号接收
    gpio_init(38,0);//灯带信号接收
    gpio_init(37,0);//炫彩灯信号接收
    gpio_init(36,0);//强光灯信号接收
    gpio_init(35,0);//氛围模式信号接收
    gpio_init(34,0);//娱乐模式信号接收
    gpio_init(33,0);//户外模式信号接收
    gpio_init(15,1);//投影灯输出
    gpio_init(14,1);//灯带输出
    gpio_init(5,1);//强光灯灯输出
    gpio_init(4,1);//炫彩灯输出
    gpio_init(30,1);//显示屏显示投影灯
    gpio_init(29,1);//显示屏显示灯带
    gpio_init(28,1);//显示屏显示炫彩灯
    gpio_init(27,1);//显示屏显示强光灯
    gpio_init(26,1);//显示屏显示氛围模式
    gpio_init(25,1);//显示屏显示娱乐模式
    gpio_init(24,1);//显示屏显示户外模式
    gpio_write(39,0);
    gpio_write(38,0);
    gpio_write(37,0);
    gpio_write(36,0);
    gpio_write(35,0);
    gpio_write(34,0);
    gpio_write(33,0);
    gpio_write(30,0);
    gpio_write(29,0);
    gpio_write(28,0);
    gpio_write(27,0);
    gpio_write(26,0);
    gpio_write(25,0);
    gpio_write(24,0);
    gpio_write(15,0);
    gpio_write(14,0);
    gpio_write(5,0);
    gpio_write(4,0);
    
    for(;;)
    {

        if(gpio_read(39))//投影灯
        {
            gpio_write(15,1);
            gpio_write(30,1);
        }
        if(gpio_read(38))//灯带
        {
            gpio_write(14,1);
            gpio_write(29,1);
        }
        if(gpio_read(37))//强光灯
        {
            gpio_write(5,1);
            gpio_write(28,1);
        }
        if(gpio_read(36))//炫彩灯
        {
            gpio_write(4,1);
            gpio_write(27,1);
        }
        if(gpio_read(35))//氛围模式
        {
            gpio_write(15,1);
            gpio_write(14,1);
            gpio_write(26,1);
        }
        if(gpio_read(34))//娱乐模式
        {
            gpio_write(14,1);
            gpio_write(5,1);
            gpio_write(25,1);
        }
        if(gpio_read(33))//户外模式
        {
            gpio_write(14,1);
            gpio_write(4,1);
            gpio_write(24,1);
        }

    }
    return 0;
}

