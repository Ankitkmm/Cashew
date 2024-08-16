❓ Problem statement
Auth service is responsible for authentication and authorization of incoming requests from the Templatisation service and API Gateway.
✨ Functional Requirements
* User should be able to Sign up and login
* User would not be asked to login everytime whenever he/she opens the app
* Store encrypted passwords in the database
* Access tokens and refresh tokens should be allotted
* Tokens should be passed over HTTPs requests
* Event published to userService should be recoverable and fault tolerant
✨ Non Functional requirements
* Authentication should not take too much time to avoid app open lag
* Database should be designed in such a way to avoid the complex and LRQ

<img width="1396" alt="Untitled" src="https://github.com/user-attachments/assets/6be74e2f-b756-4797-94ba-edd1836809f4">

<img width="1230" alt="Untitled (1)" src="https://github.com/user-attachments/assets/302877f5-8000-434a-9c87-dba519c89165">



* SecurityConfig:- This class is about making Beans like applying filters that a request will go through before reaching to our controllers. Defining AuthenticationProvider and other related beans to be defined here.
* JWTFilter:- It is a filter that will be applied to every request apart from the requests which are mentioned to bypass this filter in SecurityConfig class like /auth/v1/refreshToken, /auth/v1/signup, /auth/v1/login
* AuthController:- Here we will define endpoints like /auth/v1/signup, /ping
* JwtService:- It is a class which will be used to generateToken, validateToken, using claims to get userName, expiration etc
* RefreshTokenService:- It is responsible for creation and validation of refresh tokens
* UserDetailsServiceImpl:- It is responsible for signing up the user, loading/fetching a user and this class will extend the UserDetailsService of *org.springframework.security.core.userdetails* package which is a spring security package.
* AuthenticationManager:- This comes from the spring boot security package that is responsible for authenticating a user based on its username and password.

