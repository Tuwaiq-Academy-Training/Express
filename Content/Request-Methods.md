## دوال request

تطرقنا سابقًا إلى مفهوم request وهو الطلب أي أن المتصفح يقوم بطلب صفحة معيّنة أو معلومات معيّنة من server، لكن ما لم نتحدث عنه هو أنواع requests فالطلبات requests من server تكون بأحد هذهِ الآليّات GET، POST، PUT OPTION، DELETE و غيرها، كل آلية أو نوع يستخدم في حالة معيّنة كمثال يستخدم GET لطلب صفحة ويب أو لعرض معلومات من قاعدة البيانات و يعتبر GET هي الآلية التلقائية للمتصفح بحيث أنه عندما لا يتم تحديد نوع معيّن لاتباعة يقوم المتصفح بإرسال الطلب بالنوع GET أيضًا، يتم استخدام الأنواع الأخرى مثل POST لإرسال بيانات فغالبًا ما يتم استخدامها لعملية إضافة بيانات في قاعدة البيانات بينما يتم استخدام PUT أو UPDATE لتحديث بيانات في قاعدة البيانات. 


في هذا الدرس سنتعلم دوال وخصائص request في Express، لكن قبل البدء يجب أن نوضح طريقة الوصول إليها من خلال Express. 

مثال:

    app.get('/', function (req, res) {
      //your code
    })

في هذا المثال نرى أننا قمنا باستخدام دالة get بحيث نوضح بأنه عند طلب الصفحة الرئيسية  `/`  باستخدام الآلية get قم بتنفيذ التالي (الدالة المرسلة)، نلاحظ في هذهِ الدالة وجود مدخلين req الذي يمثل request و res الذي يمثل response، بالتالي في حالة أردنا الوصول إلى دوال request سنقوم باستخدام req.




### الخاصية params

هذهِ الخاصية تساعدنا للوصول إلى البيانات المرسلة عبر الرابط، كمثال عند إرسال بيانات مثل اسم الطالب في الرابط URL بهذا الشكل  `students/sara/` بحيث يكون الاسم sara هو البيانات المرسلة فسنستطيع الوصول له عبر الخاصية  `params` .


مثال:

    app.get('/user/:id', function (req, res) {
      res.send('user ' + req.params.id)
    })




### الخاصية body

هذهِ الخاصية تساعدنا للوصول إلى البيانات المرسلة عبر body الخاص بالطلب. 

مثال:

    const express = require('express')
    
    const app = express()
    
    app.use(express.json()) // for parsing application/json
    app.use(express.urlencoded({ extended: true })) // for parsing application/x-www-form-urlencoded
    
    app.post('/profile', function (req, res) {
      res.json(req.body)
    })

من خلال استخدام req.body يمكننا الوصول إلى البيانات المرسلة في body لكن نلاحظ السطرين البرمجيين بالأعلى.


    app.use(express.json()) // for parsing application/json
    app.use(express.urlencoded({ extended: true })) // for parsing application/x-www-form-urlencoded

 تم استخدام express.json لعملية parsing لأن Express لا يقوم بدعم إرسال بيانات عبر body بشكل تلقائي. 


