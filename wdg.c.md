#include "wdg.h"
#include "ls1c102.h"
#include "stdint.h"

extern HW_PMU_t *g_pmu;

void WdgInit(void)
{
    WDG_SetWatchDog(0x80007fff);
    WDG_DogFeed();
}
void WDG_SetWatchDog(uint32_t time)
{
    WDG_DogFeed();
    g_pmu->WdtCfg = ((~time)<<16 | time);
}
void WDG_DogFeed(void)
{
    g_pmu->WdtFeed = WDTFEED_FOOD;
}
void my_delay(volatile int i)
{
    while(i--);
}




