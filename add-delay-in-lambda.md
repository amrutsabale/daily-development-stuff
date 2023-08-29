````
const task = new Promise((resolve) => {
        setTimeout(async () => {
          await svc.perform({
            user_id
          });         
          resolve({ statusCode: 200, message: 'Task finished.' });
        }, 360000);//6 min
      });

      const res = await task;

````
