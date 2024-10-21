# JPP SIG

**Folder Structure**

3. **Different Config Files per Environment**:
   - Create separate configuration files for each environment (e.g., `config.dev.json`, `config.prod.json`), and load the appropriate file based on the environment the application is running in.
   - Example:
     ```
     /config
       config.dev.json
       config.prod.json
       config.test.json
     ```

4. **Centralize Configuration Loading**:
   - Create a central module or function in your application that loads configuration settings from files or environment variables. This module should handle validation and provide default values if needed.
   - Example (Node.js):
     ```javascript
     const dotenv = require('dotenv');
     dotenv.config();

     const config = {
       dbUrl: process.env.DATABASE_URL || 'localhost',
       apiKey: process.env.API_KEY || '',
       logLevel: process.env.LOG_LEVEL || 'info'
     };

     module.exports = config;
     ```

5. **Avoid Hardcoding Configuration Values**:
   - Never hardcode configuration values directly into your application logic. Instead, use environment variables or load them from configuration files.
   - **Bad Practice**:
     ```javascript
     const dbUrl = 'localhost:5432/mydb'; // Hardcoded database URL
     ```
   - **Good Practice**:
     ```javascript
     const dbUrl = process.env.DATABASE_URL; // Load from environment variable
     ```
### 14. Use Configuration Management Tools (Shall)

For large-scale applications, it is essential to use a **configuration management tool** to handle dynamic configurations across distributed systems. As applications scale, managing configuration via hardcoded values or static configuration files becomes inefficient and prone to errors. Configuration management tools allow for centralized, secure, and dynamic management of environment-specific settings such as API keys, database connections, and feature flags.

#### Common Configuration Management Tools:
- **Consul**: A tool for service discovery and configuration management.
- **etcd**: A distributed key-value store that provides a reliable way to store and access configuration data across a cluster.
- **AWS Systems Manager Parameter Store**: A service that enables secure management of parameters and secrets for AWS infrastructure.
- **Vault**: For managing secrets, encryption keys, and access to sensitive data.

These tools help manage configuration at scale, ensuring consistency across environments and reducing the risk of configuration-related issues during deployment.

---

#### Example of Configuration Separation:

**Directory Structure**:
```
/my-app
  /config
    config.dev.json
    config.prod.json
  /src
    index.js
  .env
```
