# Ex9 Applications of Queue - SJF
## DATE:
## AIM:
To incorporate the code to calculate the Total Waiting Time and Average Waiting Time in Shortest Job First scheduling algorithm.
## Algorithm
1. Start the program.
2. Read the number of processes n and their burst times into the array bt[].
3. Assign process numbers to array p[] (from 1 to n).
4. Sort the processes based on burst time using selection sort, updating both bt[] and p[] arrays.
5. Calculate the waiting time wt[] for each process by summing burst times of previous processes.
6. Calculate the turnaround time tat[] as the sum of burst time and waiting time for each process.
7. Compute and print the average waiting time and average turnaround time.
8. End the program. 

## Program:
```
/*
Program to find the Total Waiting Time and Average Waiting Time in Shortest Job First scheduling algorithm.
Developed by: PAVITHRA S
RegisterNumber: 212223230147
*/
/*
#include<stdio.h> 
int main() 
{ 
int bt[20],p[20],wt[20],tat[20],i,j,n,total=0,pos,temp; 
float avg_wt,avg_tat; 
scanf("%d",&n); 
for(i=0;i<n;i++) 
{ 
scanf("%d",&bt[i]); 
p[i]=i+1; 
} 
for(i=0;i<n;i++) 
{ 
pos=i; 
for(j=i+1;j<n;j++) 
{ 
if(bt[j]<bt[pos]) 
pos=j; 
} 
  
  
 
temp=bt[i]; 
bt[i]=bt[pos]; 
bt[pos]=temp; 
 
temp=p[i]; 
p[i]=p[pos]; 
p[pos]=temp; 
} 
 
wt[0]=0; 
for(i=1;i<n;i++) 
{ 
wt[i]=0; 
for(j=0;j<i;j++) 
wt[i]+=bt[j]; 
total+=wt[i]; 
} 
 
avg_wt=(float)total/n; 
total=0; 
printf("Process Burst Time Waiting Time Turnaround Time\n"); 
for(i=0;i<n;i++) 
{ 
tat[i]=bt[i]+wt[i]; //calculate turnaround time 
total+=tat[i]; 
//printf("\n"); 
printf("p%d %d %d %d\n",p[i],bt[i],wt[i],tat[i]); 
} 
 
avg_tat=(float)total/n; //average turnaround time 
// printf("\n"); 
printf("Average Waiting Time=%f\n",avg_wt); 
// printf("\n"); 
printf("Average Turnaround Time=%f\n",avg_tat); 
return 0; 
}
```

## Output:
![image](https://github.com/user-attachments/assets/824b3a1a-fbff-4a88-8628-ed7c21ebd070)



## Result:
Thus, the code to calculate the Total Waiting Time and Average Waiting Time in Shortest Job First scheduling algorithm is implemented successfully.
