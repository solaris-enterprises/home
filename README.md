# Solaris Backendend API Specification

This is the outline for a solaris backend website. The frontend/UI will be created separately. In absence of any fronend, this API can be tested using tools such as **Postman**. All of the functionality below needs to be fully implmented in this project.


### JOB_BANK
- List all Jobs in the database
   * Pagination
   * Select specific fields in result
   * Limit number of results
   * Filter by fields
- Search Jobs based on following parameters
  * Salary
  * Location
  * working benifits
  * Skills
  * working condition
  * Workplace facilities
  * Job role
  * Growth Prospect
- Add jobs (For authorized personel only)
  * Provide detailed descriptions for the position
- Update Job
  * Owner only
  * Validation on update
- Delete Job
  * Owner only


### CANDIDATE_BANK
- List all Candidates in the database (For authorised personel only)
   * Pagination
   * Select specific fields in result
   * Limit number of results
   * Filter by fields
- Search Candidates based on following parameters (For authorised personel only)
  * (To be planned)
- Add Candidate
  * Owner only
  * Validation on update
- Delete Candidate
  * Owner only
- Update Candidate
  * Owner only
 
### MATCHING_MODULE
- Calculate various metrics
- Produce relevant charts
- List out candidates based on job requirements
- List out jobs based on candidate's inputs 

### INTERVIEW_MODULE
- Add Questionnaire
- Edit Questionnaire 
- Delete Questionnaire
- Add Test
- Edit test
- Delete Test
- List all test results
  * Pagination, filtering, etc
- Get individual reports
### Feedback
- Candidate feedback 
  * on Platform
  * on Employer
- Employer feedback 
  * on Platform
  * on Candidate

### Users & Authentication
- Authentication will be ton using JWT/cookies
  * JWT and cookie should expire in 30 days
- User registration
  * Register as a **Employer** or  **Candidate**
  * Once registered, a token will be sent along with a cookie (token = xxx)
  * Passwords must be hashed
- User login
  * User can login with email and password
  * Plain text password will compare with stored hashed password
  * Once logged in, a token will be sent along with a cookie (token = xxx)
- User logout
  * Cookie will be sent to set token = none
- Get user
  * Route to get the currently logged in user (via token)
- Password reset (lost password)
  * User can request to reset password
  * A hashed token will be emailed to the users registered email address
  * A put request can be made to the generated url to reset password
  * The token will expire after 10 minutes
- Update user info
  * Authenticated user only
  * Separate route to update password
- User CRUD
  * Admin only
- Users can only be made admin by updating the database field manually

## Security
- Encrypt passwords and reset tokens
- Prevent cross site scripting - XSS
- Prevent NoSQL injections
- Add a rate limit for requests of 100 requests per 10 minutes
- Protect against http param polution
- Add headers for security (helmet)
- Use cors to make API public (for now)
## Payemnt
- (To be planned after payment solution is finalised)

## Documentation
- Use Postman to create documentation
- Use docgen to create HTML files from Postman
- Add html files as the / route for the api

## Deployment 
- Push to Github
- Clone repo on to server (AWS /AZURE /DIGITAL Ocean E.T.C.) 
- Connect a domain name
- Install an SSL using Let's Encrypt

## Code Related Suggestions
- NPM scripts for dev and production env
- Config file for important constants
- Use controller methods with documented descriptions/routes
- Error handling middleware
- Authentication middleware for protecting routes and setting user roles
- Validation using Mongoose and no external libraries
- Use async/await (create middleware to clean up controller methods)
- Create a database seeder to import and destroy data
