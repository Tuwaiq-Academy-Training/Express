## دوال response

دوال response هي المستخدمة للرد على طلب client، ونستخدمها عند التعامل مع الطلبات مثل الرد عند طلب المتصفح صفحة معينة وللوصول إلى دوال response من خلال Express سنقوم باستخدام المدخل الثاني من الدالة المرسلة وهو  `res`  في المثال التالي: 

    app.get('/', function (req, res) {
      //your code
    })



### دالة redirect

تقوم هذهِ الدالة باعادة توجيه المستخدم إلى صفحة أخرى كمثال، عند طلب المستخدم صفحة  `users/`  نستطيع إعادة توجيهه إلى صفحة أخرى أو موقع آخر باستخدام الدالة redirect.

تعريف الدالة:

    res.redirect([status,] path)

تستقبل الدالة status وهو رقم الحالة التي تريد الرد بها مع المسار (الرابط) الذي ستوجه المستخدم له.

مثال 1:

    app.get('/', function (req, res) {
      res.redirect('/users')
    })

مثال 2:

    app.get('/', function (req, res) {
      res.redirect(301,'/users')
    })


> ملاحظة: الرقم التلقائي للحالة status code هو 302، أي found.

مثال 3:

    app.get('/', function (req, res) {
      res.redirect('http://google.com')
    })



### دالة render

تقوم دالة render باستقبال صفحة لعرضها كرد على الطلب. 

تعريف الدالة:

    res.render(view [, locals] [, callback])

مثال:

    app.get('/', function (req, res) {
      res.render('index')
    })



### دالة send

ستقوم هذهِ الدالة بارسال رد سواء كان هذا الرد مجرد نص أو بيانات json أو حتى عنصر html.

تعريف الدالة:

    res.send([body])

مثال 1:

    app.get('/', function (req, res) {
      res.send('<p>Hello world!</p>')
    })

مثال 2:

    app.get('/', function (req, res) {
      res.send('just a text')
    })

مثال 3:

    app.get('/', function (req, res) {
      res.send({greeting:'hello'})
    })


### دالة status

تقوم دالة status بتحديد رقم الحالة المناسب كرد للطلب.

تعريف الدالة:

    res.status(code)

مثال 1:

    app.get('/', function (req, res) {
      res.status(404)
      res.send('page not found')
    })

مثال 2:

    app.get('/', function (req, res) {
      res.status(200)
    })


