# Local database and demo data

The application creates or updates the schema on startup with `spring.jpa.hibernate.ddl-auto=update`. To create it manually, run `schema.sql` in MySQL Workbench as a database administrator.

Demo accounts use passwords chosen locally; the project ships no default credentials.

1. Set `UDHARI_ADMIN_EMAIL` and `UDHARI_ADMIN_PASSWORD` in the ignored `.env` file before the first app startup. The app creates the first ADMIN only when no ADMIN account exists.
2. Register a borrower through `POST /api/auth/register` using a private password you choose:

   ```json
   {
     "email": "borrower@example.test",
     "password": "replace-with-a-private-password",
     "fullName": "Demo Borrower",
     "monthlyIncome": 50000,
     "employmentType": "Salaried"
   }
   ```

3. Sign in as the borrower, apply for INR 50,000 over 12 months, then sign in as the configured admin to approve the application. Approval creates the schedule. Mark each pending instalment paid to demonstrate repayment tracking and loan closure.

Replace the sample password before sending the request. Do not commit `.env` or share its values.
