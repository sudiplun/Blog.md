#### C Program to simulate the following CPU Scheduling Algorithms

##### First Come First Serve (FCFS)

```c
#include<stdio.h>
int main() {
   int bt[20], p[20], wt[20], tat[20], i, j, n, total = 0, pos, temp;
   float avg_wt, avg_tat;
   printf("Enter number of process:");
   scanf("%d", & n);
   printf("\nEnter Burst Time:\n");
   for (i = 0; i < n; i++) {
      printf("p % d:", i + 1);
      scanf("%d", & bt[i]);
      p[i] = i + 1; //contains process number
   }
   wt[0] = 0; //waiting time for first process will be zero
   //calculate waiting time
   for (i = 1; i < n; i++) {
      wt[i] = 0;
      for (j = 0; j < i; j++)
         wt[i] += bt[j];
      total += wt[i];
   }
   avg_wt = (float) total / n; //average waiting time
   total = 0;
   printf("\nProcess\t Burst Time \tWaiting Time\tTurnaround Time");
   for (i = 0; i < n; i++) {
      tat[i] = bt[i] + wt[i]; //calculate turnaround time
      total += tat[i];
      printf("\np%d\t\t %d\t\t %d\t\t\t%d", p[i], bt[i], wt[i], tat[i]);
   }
   avg_tat = (float) total / n; //average turnaround time
   printf("\n\nAverage Waiting Time=%f", avg_wt);
   printf("\nAverage Turnaround Time=%f\n", avg_tat);
}
```

##### SJF (Shortest Job First)

```C
#include<stdio.h>
int main() {
   int bt[20], p[20], wt[20], tat[20], i, j, n, total = 0, pos, temp;
   float avg_wt, avg_tat;
   printf("Enter number of process:");
   scanf("%d", & n);
   printf("\nEnter Burst Time:\n");
   for (i = 0; i < n; i++) {
      printf("p%d:", i + 1);
      scanf("%d", & bt[i]);
      p[i] = i + 1; //contains process number
   }
   //sorting burst time in ascending order using selection sort
   for (i = 0; i < n; i++) {
      pos = i;
      for (j = i + 1; j < n; j++) {
         if (bt[j] < bt[pos])
            pos = j;
      }
      temp = bt[i];
      bt[i] = bt[pos];
      bt[pos] = temp;
      temp = p[i];
      p[i] = p[pos];
      p[pos] = temp;
   }
   wt[0] = 0; //waiting time for first process will be zero
   //calculate waiting time
   for (i = 1; i < n; i++) {
      wt[i] = 0;
      for (j = 0; j < i; j++)
         wt[i] += bt[j];
      total += wt[i];
   }
   avg_wt = (float) total / n; //average waiting time
   total = 0;
   printf("\nProcess\t Burst Time \tWaiting Time\tTurnaround Time");
   for (i = 0; i < n; i++) {
      tat[i] = bt[i] + wt[i]; //calculate turnaround time
      total += tat[i];
      printf("\np%d\t\t %d\t\t %d\t\t\t%d", p[i], bt[i], wt[i], tat[i]);
   }
   avg_tat = (float) total / n; //average turnaround time
   printf("\n\nAverage Waiting Time=%f", avg_wt);
   printf("\nAverage Turnaround Time=%f\n", avg_tat);
}
```

##### Round Robin(RR)

```c
#include <stdio.h>
main()
  {
    int st[10], bt[10], wt[10], tat[10], n, tq;
    int i, count = 0, swt = 0, stat = 0, temp, sq = 0;
    float awt, atat;
    printf("enter the number of processes");
    scanf("%d", &n);
    printf("enter the burst time of each process /n");
    for (i = 0; i < n; i++)
    {
      printf(("p%d", i + 1); scanf("%d", &bt[i]); st[i] = bt[i];
      }
      printf("enter the time quantum");
      scanf("%d", &tq);
      while (1)
      {
        for (i = 0, count = 0; i < n; i++)
        {
          temp = tq;
          if (st[i] == 0)
          {
            count++;
            continue;
          }
          if (st[i] > tq)
            st[i] = st[i] - tq;
          else
          if (st[i] >= 0)
          {
            temp = st[i];
            st[i] = 0;
          }
          sq = sq + temp;
          tat[i] = sq;
        }
        if (n == count)
          break;
      }
      for (i = 0; i < n; i++)
      {
        wt[i] = tat[i] - bt[i];
        swt = swt + wt[i];
        stat = stat + tat[i];
      }
      awt = (float) swt / n;
      atat = (float) stat / n;
      printf("process no\t burst time\t waiting time\t turnaround time\n");
      for (i = 0; i < n; i++)
        printf("%d\t\t %d\t\t %d\t\t %d\n", i + 1, bt[i], wt[i], tat[i]);
      printf("avg wt time=%f,avg turn around time=%f", awt, atat);
    }
```

##### Priority Scheduling

```c
#include <stdio.h>
int main()
{
  int bt[20], p[20], wt[20], tat[20], pri[20], i, j, k, n, total = 0, pos, temp;
  float avg_wt, avg_tat;
  printf("Enter number of process:");
  scanf("%d", &n);
  printf("\nEnter Burst Time:\n");
  for (i = 0; i < n; i++)
  {
    printf("p%d:", i + 1);
    scanf("%d", &bt[i]);
    p[i] = i + 1;	//contains process number
  }

  printf(" enter priority of the process ");
  for (i = 0; i < n; i++)
  {
    p[i] = i;
   	//printf("Priority of Process");
    printf("p%d ", i + 1);
    scanf("%d", &pri[i]);
  }
  for (i = 0; i < n; i++)
  {
    for (k = i + 1; k < n; k++)
    {
      if (pri[i] > pri[k])
      {
        temp = p[i];
        p[i] = p[k];
        p[k] = temp;
        temp = bt[i];
        bt[i] = bt[k];
        bt[k] = temp;
        temp = pri[i];
        pri[i] = pri[k];
        pri[k] = temp;
      }
    }
  }

  wt[0] = 0;	//waiting time for first process will be zero
 	//calculate waiting time
  for (i = 1; i < n; i++)
  {
    wt[i] = 0;
    for (j = 0; j < i; j++)
    {
      wt[i] += bt[j];
      total += wt[i];
    }
    avg_wt = (float) total / n;	//average waiting time
    total = 0;
  }

  printf("\nProcess\t Burst Time \tPriority \tWaiting Time\tTurnaround Time");
  for (i = 0; i < n; i++)
  {
    tat[i] = bt[i] + wt[i];	//calculate turnaround time
    total += tat[i];
    printf("\np%d\t\t %d\t\t %d\t\t %d\t\t\t%d", p[i], bt[i], pri[i], wt[i], tat[i]);
  }
  avg_tat = (float) total / n;	//average turnaround time
  printf("\n\nAverage Waiting Time=%f", avg_wt);
  printf("\nAverage Turnaround Time=%f\n", avg_tat);
}
```

#### C Program to simulate Bankers Algorithm for:

##### Bankers Algorithm for Deadlock Avoidance

```c
#include <stdio.h>
int main()
  {
    int allocated[15][15], max[15][15], need[15][15], avail[15], tres[15], work[15], int pno, rno, i, j, prc, count, t, total;
    count = 0;
   	//clrscr ();
    printf("\n Enter number of process:");
    scanf("%d", &pno);
    printf("\n Enter number of resources:");
    scanf("%d", &rno);
    for (i = 1; i <= pno; i++)
      flag[i] = 0;
    printf("\n Enter total numbers of each resources:");
    for (i = 1; i <= rno; i++)
    {
      scanf("%d", &tres[i]);
    }
    printf("\n Enter Max resources for each process:");
    for (i = 1; i <= pno; i++)
    {
      printf("\n for process %d:", i);
      for (j = 1; j <= rno; j++)
        scanf("%d", &max[i][j]);
    }
    printf("\n Enter allocated resources for each process:");
    for (i = 1; i <= pno; i++)
    {
      printf("\n for process %d:", i);
      for (j = 1; j <= rno; j++)
        scanf("%d", &allocated[i][j]);
    }
    printf("\n available resources:\n");
    for (j = 1; j <= rno; j++)
    {
      avail[j] = 0;
      total = 0;
      for (i = 1; i <= pno; i++)
      {
        total += allocated[i][j];
      }
      avail[j] = tres[j] - total;
      work[j] = avail[j];
      printf(" %d \t", work[j]);
    }
    do {
      for (i = 1; i <= pno; i++)
      {
        for (j = 1; j <= rno; j++)
          need[i][j] = max[i][j] - allocated[i][j];
      }
      printf("\n Allocated matrix Max need”);
        for (i = 1; i <= pno; i++)
        {
          printf("\n");
          for (j = 1; j <= rno; j++)
          {
            printf("%4d", allocated[i][j]);
          }
          printf("|");
          for (j = 1; j <= rno; j++)
          {
            printf("%4d", max[i][j]);
          }
          printf("|");
          for (j = 1; j <= rno; j++)
          {
            printf("%4d", need[i][j]);
          }
        }
        prc = 0;
        for (i = 1; i <= pno; i++)
        {
          if (flag[i] == 0)
          {
            prc = i;
            for (j = 1; j <= rno; j++)
            {
              if (work[j] < need[i][j])
              {
                prc = 0;
                break;
              }
            }
          }
          if (prc != 0)
            break;
        }
        if (prc != 0)
        {
          printf("\n Process %d completed", i);
          count++;
          printf("\n Available matrix:");
          for (j = 1; j <= rno; j++)
          {
            work[j] += allocated[prc][j];
            allocated[prc][j] = 0;
            max[prc][j] = 0;
            flag[prc] = 1;
            printf(" %d", work[j]);
          }
        }
      }
      while (count != pno && prc != 0);
      if (count == pno)
        printf("\nThe system is in a safe state!!");
      else
        printf("\nThe system is in an unsafe state!!");
      return 0;
    }
```

##### Bankers Algorithm for Deadlock Prevention

```c
#include <stdio.h>
int max[10][10], alloc[10][10], need[10][10], avail[10], i, j, p, r, finish[10] = { 0
}, flag = 0;
main()
  {
    printf("\n SIMULATION OF DEADLOCK PREVENTION \n ");
    printf("Enter no. of processes, resources\n ");
    scanf("%d%d", &p, &r);
    printf("Enter allocation matrix");
    for (i = 0; i < p; i++)
      for (j = 0; j < r; j++)
        scanf("%d", &alloc[i][j]);
    printf("\n enter max matrix");
    for (i = 0; i < p; i++) /*reading the maximum matrix and availale matrix*/
      for (j = 0; j < r; j++)
        scanf("%d", &max[i][j]);
    printf(" \n enter available matrix");
    for (i = 0; i < r; i++) scanf("%d", &avail[i]);
    for (i = 0; i < p; i++)
      for (j = 0; j < r; j++)
        need[i][j] = max[i][j] - alloc[i][j];
    fun(); /*calling function*/
    if (flag == 0)
    {
      if (finish[i] != 1)
      {
        printf("\n Failing :Mutual exclusion");
        for (j = 0; j < r; j++)
        { /*checking for mutual exclusion*/
          if (avail[j] < need[i][j])
            avail[j] = need[i][j];
        }
        fun();
        printf("\n By allocating required resources to process %d dead lock is preventedprintf("\
          n lack of preemption ");
          for (j = 0; j < r; j++)
          {
            if (avail[j] < need[i][j])
              avail[j] = need[i][j];
            alloc[i][j] = 0;
          }
          fun(); printf("\n dead lock is prevented by allocating needed resources"); printf(" \n failing:Hold and Wait condition ");
          for (j = 0; j < r; j++)
          { /*checking hold and wait condition*/
            if (avail[j] < need[i][j])
              avail[j] = need[i][j];
          }
          fun(); printf("\n AVOIDING ANY ONE OF THE CONDITION, U CAN PREVENT
            DEADLOCK ");
    }
        }
        fun()
          {
            while (1)
            {
              for (flag = 0, i = 0; i < p; i++)
              {
                if (finish[i] == 0)
                {
                  for (j = 0; j < r; j++)
                  {
                    if (need[i][j] <= avail[j])
                      continue;
                    else
                      break;
                  }
                  if (j == r)
                  {
                    for (j = 0; j < r; j++)
                      avail[j] += alloc[i][j];
                    flag = 1;
                    finish[i] = 1;
                  }
                }
              }
```

#### C Program to implement the Producer-Consumer problem using Semaphores (Using UNIX/LINUX) System Calls.

```c
#include <stdio.h>
#include <stdlib.h>
int mutex = 1, full = 0, empty = 3, x = 0;
int main()
{
  int n;
  void producer();
  void consumer();
  int wait(int);
  int signal(int);
  printf("\n1.Producer\n2.Consumer\n3.Exit");
  while (1)
  {
    printf("\nEnter your choice:");
    scanf("%d", &n);
    switch (n)
    {
      case 1:
        if ((mutex == 1) && (empty != 0))
          producer();
        else
          printf("Buffer is full!!");
        break;
      case 2:
        if ((mutex == 1) && (full != 0))
          consumer();
        else
          printf("Buffer is empty!!");
        break;
      case 3:
        exit(0);
        break;
    }
  }
  return 0;
}
int wait(int s)
{
  return (--s);
}
int signal(int s)
{
  return (++s);
}
void producer()
{
  mutex = wait(mutex);
  full = signal(full);
  empty = wait(empty);
  x++;
  printf("\nProducer produces the item %d", x);
  mutex = signal(mutex);
}
void consumer()
{
  mutex = wait(mutex);
  full = wait(full);
  empty = signal(empty);
  printf("\nConsumer consumes item %d", x);
  x--;
  mutex = signal(mutex);
}
```

#### C Program to illustrate the Following IPC mechanism:

##### PIPE PROCESSING

```c
#include <unistd.h>
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#define MSG_LEN 64 int main()
  {
    int result;
    int fd[2];
    char message[MSG_LEN];
    char recvd_msg[MSG_LE];
    result = pipe(fd);
   	//Creating a pipe//fd[0] is for reading and fd[1] is for writing
    if (result < 0)
    {
      perror("pipe ");
      exit(1);
    }
    strncpy(message, "Linux World!! ", MSG_LEN);
    result = write(fd[1], message, strlen(message));
    if (result < 0)
    {
      perror("write");
      exit(2);
    }
    strncpy(message, "Understanding ", MSG_LEN);
    result = write(fd[1], message, strlen(message));
    if (result < 0)
    {
      {
        perror("write");
        exit(2);
      }
      strncpy(message, "Concepts of ", MSG_LEN);
      result = write(fd[1], message, strlen(message));
      if (result < 0)
      {
        perror("write");
        exit(2);
      }
      strncpy(message, "Piping ", MSG_LEN);
      result = write(fd[1], message, strlen(message));
      if (result < 0)
      {
        perror("write");
        exit(2);
      }
      result = read(fd[0], recvd_msg, MSG_LEN);
      if (result < 0)
      {
        perror("read");
        exit(3);
      }
      printf("%s\n", recvd_msg);
      return 0;
    }
```

##### FIFO

```c
#include <stdio.h>
#include <stdlib.h>
#include <sys/stat.h>
#include <unistd.h>
#include <linux/stat.h>
#define FIFO_FILE“ MYFIFO”
int main(void)
{
  FILE * fp;
  char readbuf[80];
  /*Create the FIFO if it does not exist */
  umask(0);
  mknod(FIFO_FILE, S_IFIFO | 0666, 0);
  while (1)
  {
    fp = fopen(FIFO_FILE, "r");
    fgets(readbuf, 80, fp);
    printf("Received string: %s\n", readbuf);
    fclose(fp);
  }
  return (0);
}
#include <stdio.h>
#include <stdlib.h>
#define FIFO_FILE "MYFIFO"
int main(int argc, char *argv[])
{
  FILE * fp;
  if (argc != 2)
  {
    printf("USAGE: fifoclient[string]\n");
    exit(1);
  }
  if ((fp = fopen(FIFO_FILE, "w")) == NULL)
  {
    perror("fopen");
    exit(1);
  }
  fputs(argv[1], fp);
  fclose(fp);
  return (0);
}
```

##### Message Queue (Writer Process)

```c
#include <stdio.h>
#include <sys/ipc.h>
#include <sys/msg.h>
	// structure for message queue
struct mesg_buffer
{
  long msg_type;
  char msg_text[100];
}
message;
int main()
{
  key_t key;
  int msgid;
 	// ftok to generate unique key
  key = ftok("progfile", 65);
 	// msgget creates a message queue
 	// and returns identifier
  msgid = msgget(key, 0666 | IPC_CREAT);
  message.mesg_type = 1;
  printf("Write Data : ");
  gets(message.mesg_text);
 	// msgsnd to send message
  msgsnd(msgid, &message, sizeof(message), 0);
 	// display the message
  printf("Data send is : %s \n", message.mesg_text);
  return 0;
}
```

#### C Program to simulate the following Memory Management Techniques

##### Paging Techniques

```c
#include <stdio.h>
#include <conio.h>
main()
{
  int ms, ps, nop, np, rempages, i, j, x, y, pa, offset;
  int s[10], fno[10][20];
  printf("\nEnter the memory size -- ");
  scanf("%d", &ms);
  printf("\nEnter the page size -- ");
  scanf("%d", &ps);
  nop = ms / ps;
  printf("\nThe no. of pages available in memory are -- %d ", nop);
  printf("\nEnter number of processes -- ");
  scanf("%d", &np);
  rempages = nop;
  for (i = 1; i <= np; i++)
  {
    printf("\nEnter no. of pages required for p[%d]-- ", i);
    scanf("%d", &s[i]);
    if (s[i] > rempages)
    {
      printf("\nMemory is Full");
      break;
    }
    rempages = rempages - s[i];
    printf("\nEnter pagetable for p[%d] --- ", i);
    for (j = 0; j < s[i]; j++)
      scanf("%d", &fno[i][j]);
  }
  printf("\nEnter Logical Address to find Physical Address ");
  printf("\nEnter process no. and pagenumber and offset -- ");
  scanf("%d %d %d", &x, &y, &offset);
  if (x > np || y >= s[i] || offset >= ps)
    printf("\nInvalid Process or Page Number or offset");
  else
  {
    pa = fno[x][y] *ps + offset;
    printf("\nThe Physical Address is -- %d", pa);
  }
}
getch();
}
```

##### Page Segmentation

```c
#include <stdio.h>
#include <conio.h>
struct list
{
  int seg;
  int base;
  int limit;
  struct list * next;
}*p;
void insert(struct list *q, int base, int limit, int seg)
{
  if (p == NULL)
  {
    p = malloc(sizeof(Struct list));
    p->limit = limit;
    p->base = base;
    p->seg = seg;
    p->next = NULL;
  }
  else
  {
    While(q->next != NULL)
    {
      q = q->next;
      printf(“yes”)
    }
    q->next = malloc(sizeof(Struct list));
    q->next->limit = limit;
    q->next->base = base;
    q->next->seg = seg;
    q->next->next = NULL;
  }
}
int find(struct list *q, int seg)
{
  while (q->seg != seg)
  {
    q = q->next;
  }
  return q->limit;
}
int search(struct list *q, int seg)
{
  while (q->seg != seg)
  {
    q = q->next;
  }
  return q->base;
}
main()
{
  p = NULL;
  int seg, offset, limit, base, c, s, physical;
  printf(“Enter segment table / n”);
  printf(“Enter - 1 as segment value
    for termination\ n”);
  do {
    printf(“Enter segment number”);
    scanf(“ % d”, &seg);
    if (seg != -1)
    {
      printf(“Enter base value: ”);
      scanf(“ % d”, &base);
      printf(“Enter value
        for limit: ”);
      scanf(“ % d”, &limit);
      insert(p, base, lmit, seg);
    }
  }
  while (seg != -1)
  {
    printf(“Enter offset: ”);
    scanf(“ % d”, &offset);
    printf(“Enter bsegmentation number: ”);
    scanf(“ % d”, &seg);
    c = find(p, seg);
    s = search(p, seg);
    if (offset< c)
    {
      physical = s + offset;
      printf(“Address in physical memory % d\ n”, physical);
    }
    else
    {
      printf(“error”);
    }
  }
}
```
