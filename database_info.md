# Database and Login Information

## Database Information

This application currently uses a mock database for demonstration purposes. The mock database is implemented in `src/lib/db/mockDatabase.ts` and simulates database operations with in-memory data.

### Mock Database Structure

The mock database contains the following collections:

1. **Inventory**: Products with details like name, price, quantity, etc.
2. **Sales**: Sales transactions with items, quantities, and totals
3. **Branches**: Supermarket branch information
4. **Users**: User accounts with roles and permissions

### Database Methods

The mock database provides methods for:
- CRUD operations for inventory items
- Recording and retrieving sales
- Managing branches
- User authentication and management
- Generating reports

### Production Database Recommendations

For a production environment, we recommend:

1. **MySQL or PostgreSQL**:
   - Good for structured data with relationships
   - Strong transaction support
   - Reliable and well-established

2. **MongoDB**:
   - Flexible schema for evolving data structures
   - Good performance for read-heavy operations
   - Easy scaling

### Database Connection

To connect to a real database:
1. Install the appropriate database driver (e.g., `mysql2`, `pg`, or `mongodb`)
2. Update the database connection in `src/lib/db/database.ts`
3. Modify the API routes to use the real database instead of the mock database

## Login Information

### Default User Accounts

| Username | Password | Role | Email |
|----------|----------|------|-------|
| admin | admin123 | Administrator | admin@supermarket.com |
| manager | manager123 | Branch Manager | manager@supermarket.com |
| cashier | cashier123 | Cashier | cashier@supermarket.com |
| inventory | inventory123 | Inventory Manager | inventory@supermarket.com |

### User Roles and Permissions

1. **Administrator**:
   - Full access to all system features
   - Can manage users, branches, and system settings
   - Can view all reports and data across branches

2. **Branch Manager**:
   - Can manage inventory and sales for their branch
   - Can view reports for their branch
   - Limited access to user management (can't create admin users)

3. **Cashier**:
   - Can process sales transactions
   - Can view basic inventory information
   - Limited access to reports

4. **Inventory Manager**:
   - Can manage inventory items
   - Can view inventory reports
   - Can create purchase orders

### Authentication Implementation

The authentication system is implemented using:
1. A login page at `/login`
2. Client-side authentication state management
3. Mock authentication in development, which can be replaced with JWT or session-based authentication in production

### Adding New Users

New users can be added through the User Management page, accessible to administrators. The system allows setting:
- Username and password
- Full name and contact information
- Role assignment
- Branch assignment
- Account status (active/inactive)

## Deployment Information

For deployment to a production environment, consider:

1. **Database Setup**:
   - Set up a production database (MySQL, PostgreSQL, or MongoDB)
   - Migrate the mock data to the production database
   - Update database connection settings

2. **Environment Variables**:
   - Create a `.env` file with database credentials and other sensitive information
   - Set up environment variables in your hosting environment

3. **Authentication Security**:
   - Implement proper password hashing (bcrypt)
   - Set up JWT or session-based authentication
   - Configure HTTPS for secure communication

4. **Backup Strategy**:
   - Set up regular database backups
   - Implement a disaster recovery plan
