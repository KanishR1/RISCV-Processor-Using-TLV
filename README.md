# RISCV-ISA


```
cd /home/kanish/RISCV-ISA/riscv_isa_labs/day_1/lab1
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton_O1.o sum1ton.c
riscv64-unknown-elf-objdump -d sum1ton_O1.o | less
spike pk sum1ton_O1.o 
```

```
#include<stdio.h>
int main()
{
    int i ,sum=0,n=9;
    for (i=1;i<=n;i++)
        sum+=i;
    printf("The sum of numbers from 1 to %d is %d\n",n,sum);
    return 0;
}
```


To debug line by line
``````
spike -d pk sum1ton_O1.o
until pc 0 10184
reg 0 sp
#Press enter for line by line execution
#To check the status of the particular register
reg 0 a2
```


```
cd /home/kanish/RISCV-ISA/riscv_isa_labs/day_1/lab1
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton_Ofast.o sum1ton.c
riscv64-unknown-elf-objdump -d sum1ton_Ofast.o | less
spike pk sum1ton_Ofast.o 
```



```
cd /home/kanish/RISCV-ISA/riscv_isa_labs/day_1/lab2
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o unsignedHighest.o unsignedHighest.c 
spike  pk unsignedHighest.o 
```

```
#include<stdio.h>
#include<math.h>

int main()
{
    unsigned long long int max = (unsigned long long int)(pow(2,64)-1);
    // unsigned long long int max = (unsigned long long int)(pow(2,127)-1);
    // unsigned long long int max = (unsigned long long int)(pow(2,64)*-1);
    // unsigned long long int max = (unsigned long long int)(pow(-2,64)-1);
    // unsigned long long int max = (unsigned long long int)(pow(-2,63)-1);
    // unsigned long long int max = (unsigned long long int)(pow(2,10)-1);
    printf("Highest number represented by unsigned long long  int is %llu \n",max);
    return 0;
}
```

```
cd /home/kanish/RISCV-ISA/riscv_isa_labs/day_1/lab2
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o signedHighest.o unsignedHighest.c 
spike  pk signedHighest.o 
```

```
#include<stdio.h>
#include<math.h>

int main()
{
    long long int max = (long long int)(pow(2,63)-1);
    long long int min = (long long int)(pow(-2,63));
    printf("Highest number represented by long long  int is %lld \n",max);
    printf("Smallest number represented by long long  int is %lld \n",min);
    return 0;
}
```