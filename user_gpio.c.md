#include "ls1c102.h"
#include "user_gpio.h"
extern HW_PMU_t *g_pmu;

void gpio_init(int gpio, int io)
{
    int bit;
    if(gpio < 32)
    {
        bit = gpio;
        if(io == 0)
            g_pmu->GPIOA_OE &= ~(0x01<<bit);
        else g_pmu->GPIOA_OE |=(0x01<<bit);
    }
    else
    {
        bit = gpio -32;
    
    if(io == 0)
        g_pmu->GPIOB_OE &= ~(0x01<<bit);
    else g_pmu->GPIOB_OE |=(0x01<<bit);
    }
}
void gpio_write(int gpio, int val)
{
    int bit;
    if(gpio < 32)
    {
        bit = gpio;
        if(val == 0)
            g_pmu->GPIOA_O &= ~(0x01<<bit);
        else g_pmu->GPIOA_O |=(0x01<<bit);
    }
    else
    {
        bit = gpio - 32;
        if(val == 0)
            g_pmu->GPIOB_O &= ~(0x01<<bit);
        else g_pmu->GPIOB_O |=(0x01<<bit);
    }
}
void gpio_read(int gpio)
{
    int bit;
    if(gpio < 32)
    {
        bit = gpio;
        if((g_pmu->GPIOA_I & (0x01<<bit))==(0x01<<bit))
            return 1;
        else
            return 0;
    }
    else
    {
        bit = gpio - 32;
        if((g_pmu->GPIOB_I & (0x01<<bit))==(0x01<<bit))
            return 1;
        else
            return 0;
    }
}

