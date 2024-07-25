# Embedded Firmware Assignment

### Problem Statement 1
In a vehicle control architecture, there are multiple Electronic Control Units (ECUs) connected together through a CAN protocol. Each ECU is programmed to take care of specific functionality. MCB is one such ECU in the architecture that performs below tasks:

- Measure 8 Bigital Inputs from multiple switches / sensors in a vehicle.
- Perform defined actions based on the status of digital inputs.
- Communication with other ECU's thorugh CAN protocol.
As part of this assignment, you have to write an Interrupt Service Routine (ISR) in C language, for samplin g the Digital inputs. The ISR should perform the below functionality:
- Read the real-time status of digital input pins from a global variable **g_ReadDIpinSts**.Here, each bit in g_ReadDIpinSts represents the status of one digital input pin.
- Update the digiral input staus to a global variable **g_AppDIpinSts**, maintaining the bit position of digital inputs.
- Condition for status update in **g_AppDIpinSts** is, "The pin state of a particular digital input has to be consistent for 10 consecutive ISR calls". Here, ISR is triggered every 100mSec once.

### Expected Output:
- Code uploaded in GitHub (share the link via Internshala chat). Use below function prototype.

   

      int ISR_DIsampling(){
            			//Write your code here
            	}

### Evaluation Criteria:
- Logic used
-  Coding Standards
- Error free code


### Problem Statement 2

A Real Time Operating System is often required when an embedded system performs various event driven functionalities and FreeRTOS is one of the most ubiquitous Real Time Operating Systems for embedded systems. This assignment involves you showcasing the knowhow (or the ability to gather said knowhow) of the basic intricacies of a RTOS stack.

#### Consider the following Tasks and its corresponding Task Handle:

|  Task Prototype| Task Handle |
|--|--|
|  void ExampleTask1(void *pV);| TaskHandle_t TaskHandle_1; |
|  void ExampleTask2(void *pV);|TaskHandle_t TaskHandle_2;  |

#### Consider the following Queue and its properties:
| Property| Value|
|--|--|
| QueueHandle| QueueHandle_t Queue1;|
| Size of Queue | 5 |
| Data Type| Data_t|

#### Definition of Data_t

    typdef struct{
	    uint8_t dataID;
	    int32_t DataValue;
	    } Data_t;
### What is to be done:

- Create Tasks **ExampleTask1** and **ExampleTask2** as per above prototypes and handles. Priority will be the same and at your descrition.
- Create Queue **Queue1** with the above properties mentioned.
- **ExampleTask1** sends data to **Queue1** at a rate of once every 500ms. The delay between each send needs to be exact. The members of the structure are populated by global variables **G_DataID;** and **G_DataValue;** Assume that these variables are updated elsewhere.
- **ExampleTask2** takes data from **Queue2** whenever data is available, and applies the following logic to the data gathered:

| Condition | Action|
|--|--|
| if(dataID==0) |Delete ExampleTask2  |
| if(dataID==1) |Allow the processing of DataValue Member  |
| if(DataValue==0) |Increase the Priority of ExampleTask2 by 2 from the value given to it at creation  |
| if(DataValue==1) |Decrease the Priority of ExampleTask2 **if** previously increased |
| if(DataValue==2) |Delete ExampleTask2 |

At every evaluation, add a print statement to print out **dataID** and **DataValue**.


### Expected Output:
- Code uploaded in GitHub (share the link via internshala chat).
### Evaluation Criteria:
- Logic used
-  Coding Standards
- Error free code

#### Note: If you need clarification on the problem statements reach out to me on internshala chat.

#### Good luck :)
