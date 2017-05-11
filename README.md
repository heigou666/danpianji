# danpianji
#include "LPC11xx.h"                    // Device header
void PIOINTS_IRQHandler(void)
	{
		if((LPC_GPIO3->MIS & (1<<2)) == (1<<2))
		{
			LPC_GPIO2->DATA &=~(1<<2);
			LPC_GPIO3->IC |= (1<<3);
			
		}
	}
	int main(void)
	{
		LPC_GPIO2->DIR |=(1<<6);
		LPC_GPIO2->DIR &=~(1<<2);
		LPC_GPIO2->IE |=(1<<2);
		LPC_GPIO2->IS |=(1<<2);
		LPC_GPIO2->IEV |=(1<<2);
		NVIC_EnableIRQ(EINT3_IRQn);
		while(1)
		{
			;
		}
	}
