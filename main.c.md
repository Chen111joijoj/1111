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
    gpio_init(39,0);//ͶӰ���źŽ���
    gpio_init(38,0);//�ƴ��źŽ���
    gpio_init(37,0);//�Ųʵ��źŽ���
    gpio_init(36,0);//ǿ����źŽ���
    gpio_init(35,0);//��Χģʽ�źŽ���
    gpio_init(34,0);//����ģʽ�źŽ���
    gpio_init(33,0);//����ģʽ�źŽ���
    gpio_init(15,1);//ͶӰ�����
    gpio_init(14,1);//�ƴ����
    gpio_init(5,1);//ǿ��Ƶ����
    gpio_init(4,1);//�Ųʵ����
    gpio_init(30,1);//��ʾ����ʾͶӰ��
    gpio_init(29,1);//��ʾ����ʾ�ƴ�
    gpio_init(28,1);//��ʾ����ʾ�Ųʵ�
    gpio_init(27,1);//��ʾ����ʾǿ���
    gpio_init(26,1);//��ʾ����ʾ��Χģʽ
    gpio_init(25,1);//��ʾ����ʾ����ģʽ
    gpio_init(24,1);//��ʾ����ʾ����ģʽ
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

        if(gpio_read(39))//ͶӰ��
        {
            gpio_write(15,1);
            gpio_write(30,1);
        }
        if(gpio_read(38))//�ƴ�
        {
            gpio_write(14,1);
            gpio_write(29,1);
        }
        if(gpio_read(37))//ǿ���
        {
            gpio_write(5,1);
            gpio_write(28,1);
        }
        if(gpio_read(36))//�Ųʵ�
        {
            gpio_write(4,1);
            gpio_write(27,1);
        }
        if(gpio_read(35))//��Χģʽ
        {
            gpio_write(15,1);
            gpio_write(14,1);
            gpio_write(26,1);
        }
        if(gpio_read(34))//����ģʽ
        {
            gpio_write(14,1);
            gpio_write(5,1);
            gpio_write(25,1);
        }
        if(gpio_read(33))//����ģʽ
        {
            gpio_write(14,1);
            gpio_write(4,1);
            gpio_write(24,1);
        }

    }
    return 0;
}

