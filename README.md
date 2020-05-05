# rabbitmq-workerqueue
distribute tasks among workers using rabbitmq worker queue pattern


start docker toolbox
run below command to spin up docker container for rabbitmq

docker run -it --rm --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3-management

now start worker.js in two separate interactive shells

start new_task.js and publish messagges
for eg node new_task.js first message
       node new_task.js second message
  so on...
  
  you will tasks will be received by workers in round robin dispatching fashion
  
  
  Important points
  
  durable : true so that message does not get lost in case of server stop
  prefetch(1) - fair dispatch - ( don't dispatch a new message to a worker until it has processed and acknowledged the previous one.)
    
    
