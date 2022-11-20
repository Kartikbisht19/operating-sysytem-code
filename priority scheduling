#include<stdio.h>
#include<stdlib.h>
#include<stdbool.h>
#include<limits.h>

struct process
{
    int pid;
    int priority;
    int at, bt , ct;
    int tat , wt, rt;
    int start_time ,  bt_remaining;
};

int main()
{
    int n;
     printf("Enter the no of process:");
     scanf("%d", &n);
    
    struct process  p[n];

    printf("Enter the pid:");
    for(int i=0;i<n;i++)
    {
          scanf("%d", &p[i].pid);
    }
    
    printf("Enter the arrival time:");
    for(int i=0;i<n;i++)
    {
          scanf("%d", &p[i].at);
    }
    
    printf("Enter the burst time:");
    for(int i=0;i<n;i++)
    {
          scanf("%d", &p[i].bt);
          p[i].bt_remaining=p[i].bt;
    }

    printf("Enter the priority:");
    for(int i=0;i<n;i++)
    {
          scanf("%d", &p[i].priority);
    }

    int completed=0;
    int current_time=0;
    bool is_completed[100]={false};
    
    float sum_tat , sum_wt , sum_rt ,avg_tat , avg_wt , avg_rt;

    while(completed !=n)
    {
        int index= -1;
        int maximum = INT_MIN;

        for(int i=0;i<n;i++)
        {
            if(p[i].at<= current_time && is_completed[i]==false)
            {
                if(p[i].priority > maximum)
                {
                     maximum = p[i].priority;
                     index=i;
                }

                if(p[i].priority == maximum)
                {
                      if(p[i].at < p[index].at)
                      {
                         maximum= p[i].priority;
                         index=i;
                      }
                }
            }
        }

        if(index ==-1)
        {
            current_time++;
        }

        else
        {
            if(p[index].bt_remaining==p[index].bt)
            {
                p[index].start_time=current_time;
            }
             p[index].bt_remaining -=1;
             current_time ++;

             if(p[index].bt_remaining == 0)
             {
                p[index].ct=current_time;
                p[index].tat = p[index].ct- p[index].at;
                p[index].wt = p[index].tat - p[index].bt;
                p[index].rt = p[index].start_time - p[index].at;

                sum_tat +=p[index].tat;
                sum_wt +=p[index].wt;
                sum_rt +=p[index].rt;

                completed++;
                is_completed[index]=true;
             }

        }
    }
    
    avg_tat=sum_tat/n;
    avg_rt=sum_rt/n;
    avg_wt=sum_wt/n;
  
  printf(" Prio Pid AT BT CT TAT WT RT\n");
  for(int i=0;i<n;i++)
  {
    printf("%d  %d  %d  %d  %d  %d  %d  %d\n",p[i].priority,p[i].pid,p[i].at,p[i].bt,p[i].ct,p[i].tat,p[i].wt,p[i].rt);
  }
 printf("Average Turn Around Time: %f\n",avg_tat); 
 printf("Average Waiting Time: %f\n",avg_wt); 
 printf("Average Response Time: %f\n",avg_rt); 

return 0;

}
