# laravel5.7-email-verification

New Features in Laravel 5.7 | Optional Email Verification

Note :- Laravel 5.7 Email Verification Source Code and DB Added. Please download and run in your apache server.

Video Tutorial :- https://youtu.be/erJdVb804k0

Laravel 5.7 introduces optional email verfication. 

Please follow below steps to configure email verification in Laravel 5.7 :-

1) First of all, install Laravel 5.7 with below command :-

laravel new laravel5.7

Now Laravel 5.7 has been installed.

We can check its version with below command :-

php artisan --version

Now version is Laravel 5.7.8 so we can continue with our process.

2) Make database of name laravel5.7 as well

3) Update .env file to connect database with our laravel5.7 project like below :-

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravel5.7
DB_USERNAME=root
DB_PASSWORD=

4) Now we run below command to create users table that we will use for registeration process of user.

php artisan migrate

5) Now we run below command to add auth and create login/register blade files.

php artisan make:auth

After running this command, we can see Login/register panel has been created with below pages :-

Login Page :- http://127.0.0.1:8000/login
Register Page :- http://127.0.0.1:8000/register

6) Now we need to use some smtp testing server for testing emails. And we will use mailtrap server for it.

Open link :- https://mailtrap.io/

Create account here at mailtrap website and then login to your account.

After login, click on Demo inbox link to get username and password that we will update at .env file in our laravel5.7 project like below :-

MAIL_USERNAME=52d6855be971d0
MAIL_PASSWORD=706bb1a60c5da4

7) Update web.php file :-

Replace Auth::routes(); with Auth::routes(['verify' => true]);

8) Update User Model :-

Replace "class User extends Authenticatable"

with

class User extends Authenticatable implements MustVerifyEmail

9) Update web.php file :-

Add "->middleware('verified');" at end of below Route :-

Route::get('/home', 'HomeController@index')->name('home')

After taking all the steps, you need to register with below link :-

http://127.0.0.1:8000/register

If any error comes then restart Laravel server.

And try again register with your email id and then after submission of form, email will go to your registered email id like shown in video.

User just need to click on Verify Email Address link to verify his email to use the account.

Below Laravel link give more details of Email Verification process :-
https://laravel.com/docs/5.7/verification

