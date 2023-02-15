 ## دوال Application

يزودنا Express بالعديد من الدوال، منها دوال خاصة في Request ودوال خاصة في Response، أيضًا دوال خاصة في التطبيق Application، ففي هذا الدرس سنتعرف على بعض من الدوال الجديدة وهي الدوال الخاصة في Application.



في ملف app.js

    const express = require('express')
    const app = express() // create app object from express().

نلاحظ تعريف app وهو object يساعدنا للوصول إلى دوال express، لذلك لنستخدم أحد هذهِ الدوال وهي دالة listen. 


### دالة listen 

هذهِ الدالة تقوم بإصغاء listen إلى أحد المنافذ port بحيث نستفيد منها لتشغيل التطبيق على هذا المنفذ واستقبال request منه.

تعريف الدالة:

    app.listen([port[, host[, backlog]]][, callback])

ما يهمنا هنا هو port وهو المنفذ الذي نريد أن يستقبل التطبيق جميع requests منه، أيضًا callback وهي الدالة التي ستتنفذ إن حصل اتصال بالمنفذ port أم فشل بالتالي تفيدنا بالتحقق مما إذا نجح الاتصال أم لا.

مثال ١:

    app.listen(3000)

مثال ٢:

    app.listen(3000، ()=> console.log('express has started!'))


### دالة get

تقوم هذهِ الدالة بتحديد ما يجب عمله عندما يكون Request من نوع GET. 

تعريف الدالة:

    app.get(path, callback [, callback ...])

يمثل path المسار أو الرابط الخاص في Request، بينما يمثل callback لدالة التي نريد تنفيذها بعد استقبال هذا Request.

مثال 1:

    app.get('/', function (req, res) {
      res.send('GET request to homepage')
    })
    نلاحظ وجود مدخلين في دالة callback، وهما req ويمثّل Request و res ويمثّل Response، أي أنه حين استقبال طلب من نوع GET على المسار  /  ( أي home/root ) قم بإرسال  send  رد مناسب، وهو النّص  'GET request to homepage'.


مثال ٢:

    const express = require('express');
    const app = express();
    const port = 3000;
    
    app.listen(port,()=>{
        console.log('express has started!');
    });
    app.get('/',(req,res)=>{
        res.send('Hello this is my HOME page');    
    });

المخرجات:

![](https://paper-attachments.dropbox.com/s_CE853FFE2306B129FFFFAC88573C5AFD3FDD80ADB50AF51B79ACF4785707617C_1626260177063_Screen+Shot+1442-12-04+at+1.54.16+PM.png)


نلاحظ في المخرجات ( 1 ) أنه قمنا باستقبال طلب GET في المسار  `/`   من ثمّ قمنا بعرض نصّ ( 2 )   `Hello this is my HOME page`  من خلال استخدامنا للدالة  `res.send` .




### دالة post

تقوم هذهِ الدالة بتحديد ما يجب عمله عندما يكون Request من نوع POST.

تعريف الدالة:

    app.post(path, callback [, callback ...])

مثال:

    app.post('/', function (req, res) {
      res.send('POST request to home page')
    })




### دالة put

تقوم هذهِ الدالة بتحديد ما يجب عمله عندما يكون Request من نوع PUT.

تعريف الدالة:

    app.put(path, callback [, callback ...])

مثال:

    app.put('/', function (req, res) {
      res.send('PUT request to home page')
    })




### دالة delete

تقوم هذهِ الدالة بتحديد ما يجب عمله عندما يكون Request من نوع DELETE .

تعريف الدالة:

    app.delete(path, callback [, callback ...])

مثال:

    app.delete('/', function (req, res) {
      res.send('DELETE request to home page')
    })




### دالة set

تستخدم هذهِ الدالة لإسناد قيمة لمتغيّر.

تعريف الدالة:

    app.set(name, value)

يمثل name اسم المتغير، بينما يمثل value القيمة لهذا المتغير.

مثال:

    app.set('title', 'My Site')
    app.get('title') // "My Site"




### دالة all

للتعامل مع جميع أنواع HTTP verbs مثل ( GET, POST, PUT, DELETE …)

تعريف الدالة:

    app.all(path, callback [, callback ...])

مثال:

    app.all('/secret', function (req, res, next) {
      console.log('Accessing the secret section ...')
      next() // pass control to the next handler
    })



### دالة use

تساعد هذه الدّالة على كتابة middleware يتنفّذ مع كل Request.

تعريف الدالة:

    app.use([path,] callback [, callback...])

مثال:

    app.use(function (req, res, next) {
      console.log('Time: %d', Date.now())
      next()
    })





المصادر:
https://expressjs.com/en/4x/api.html#app.put.method
