# Postman Environment Setup for Enjoy Rewards API

  

This guide explains how to set up and use different environments in Postman for testing the Enjoy Rewards API.

  

## 📁 Files Structure

  

```

environments/

├── local.json # Local Development Environment

├── sit.json # SIT (System Integration Testing) Environment

├── uat.json # UAT (User Acceptance Testing) Environment

└── production.json # Production Environment

```

  

## 🚀 How to Set Up Environments in Postman

  

### Step 1: Import the Collection

1. Open Postman

2. Click **"Import"** button

3. Select the file: `enjoy-rewards-postman-collection.json`

4. Click **"Import"**

  

### Step 2: Import Environments

1. Click **"Import"** again

2. Select **"File"** tab

3. Choose one or more environment files:

- `local.json` - For local development

- `sit.json` - For SIT testing

- `uat.json` - For UAT testing

- `production.json` - For production testing

4. Click **"Import"**

  

### Step 3: Select Environment

1. In the top-right corner of Postman, you'll see a dropdown

2. Click the dropdown and select your desired environment:

- **Local Development** - For testing on localhost

- **SIT Environment** - For SIT testing

- **UAT Environment** - For UAT testing

- **Production Environment** - For production testing

  

## 🔧 Environment Variables

  

Each environment contains the following variables:

  

| Variable | Description | Example |

|----------|-------------|---------|

| `baseUrl` | Base URL for voucher endpoints | `http://localhost:10100/api/v5/third-party` |

| `baseAuthUrl` | Base URL for authentication | `http://localhost:10101/api/auth` |

| `trackingUrl` | Base URL for tracking endpoints | `http://localhost:10100/api/v5/mobile-tracking-event` |

| `authToken` | JWT authentication token | `Bearer eyJhbGciOiJSUzI1NiIs...` |

| `apiKeyTracker` | API key for tracking endpoints | `mobile.YOUR_API_KEY` |

| `username` | Login username | `loki` |

| `password` | Login password | `Test@123` |

| `loginSystem` | Login system type | `ETIQA_PLUS` |

  

## 🔄 Switching Between Environments

  

### Method 1: Dropdown Selection

1. Click the environment dropdown in the top-right corner

2. Select your desired environment

3. All requests will now use the selected environment's variables

  

### Method 2: Environment Manager

1. Click the **"Environments"** tab in the left sidebar

2. Click on the environment you want to use

3. Click **"Set Active"** button

  

## 🔐 Security Best Practices

  

### For Local Development

- ✅ Use real credentials for testing

- ✅ Store sensitive data in environment variables

- ✅ Use `secret` type for passwords and tokens

  

### For SIT/UAT/Production

- ⚠️ **NEVER** commit real production credentials

- ⚠️ Use placeholder values in environment files

- ⚠️ Update credentials manually after import

- ⚠️ Use team password managers for sharing credentials

  

## 📝 Updating Environment Variables

  

### Method 1: Environment Manager

1. Click **"Environments"** in the left sidebar

2. Select your environment

3. Edit variables in the table

4. Click **"Save"**

  

### Method 2: Quick Edit

1. Click the environment dropdown

2. Click **"Edit"** next to your environment

3. Make changes and save

  

### Method 3: Variable Editor

1. In any request, click on a variable (e.g., `{{baseUrl}}`)

2. Click **"Set as environment variable"**

3. Choose your environment and variable name

  

## 🔄 Auto-Update Auth Token

  

The login requests are configured to **automatically update** the `authToken` environment variable after a successful login!

  

### How It Works:

1. **Run any Login request** (ETIQA_PLUS or Default)

2. **Check the Console** (View → Show Postman Console)

3. **Token is automatically updated** - no manual work needed!

  

### What You'll See in Console:

```

🔧 Environment: Local Development

🌐 Auth URL: http://localhost:10101/api/auth

👤 Username: loki

🔑 Login System: ETIQA_PLUS

--- Starting login process ---

✅ Login successful! Auth token updated automatically.

Token: eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9...

🔄 All subsequent requests will use the new token.

```

  

### Manual Update (if needed):

If you need to manually update the token:

1. **Run the Login request first**

2. **In the response**, copy the `accessToken` value

3. **Update the environment variable**:

- Click **"Environments"** in the left sidebar

- Select your environment

- Find the `authToken` variable

- Paste the new token value

- Click **"Save"**

  

## 🧪 Testing Workflow

  

### Recommended Testing Order:

1. **Select Environment** (Local/SIT/UAT/Production)

2. **Update Credentials** if needed

3. **Run Login** to get fresh auth token

4. **Update authToken** variable with new token

5. **Test Voucher Endpoints**:

- Get Available Vouchers

- Get Voucher Details by ID

- Claim a Voucher

- Use a Voucher

6. **Test Tracking Endpoints**:

- Track Voucher Claim

- Track My Rewards Tap

- Track Use Deal Now

- Track Continue Browsing

- Track Close Deal

  

## 🚨 Troubleshooting

  

### Common Issues:

  

**1. "Variable not found" error**

- ✅ Check if environment is selected

- ✅ Verify variable name spelling

- ✅ Ensure variable is enabled in environment

  

**2. "Invalid token" error**

- ✅ Run login request first

- ✅ Update `authToken` variable with new token

- ✅ Check token expiration

  

**3. "API key invalid" error**

- ✅ Verify `apiKeyTracker` value

- ✅ Check if API key format is correct (`mobile.YOUR_KEY`)

- ✅ Ensure API key is valid for the environment

  

**4. "Connection refused" error**

- ✅ Check if local server is running (for local environment)

- ✅ Verify URL is correct for the environment

- ✅ Check network connectivity

  

## 📋 Environment Checklist

  

Before testing, ensure:

  

- [ ] Environment is selected in Postman

- [ ] All required variables are set

- [ ] Credentials are valid for the environment

- [ ] Auth token is fresh (run login if needed)

- [ ] API keys are correct for the environment

- [ ] URLs are accessible

  

## 🔗 Useful Links

  

- [Postman Environment Variables Guide](https://learning.postman.com/docs/sending-requests/variables/)

- [Postman Collection Runner](https://learning.postman.com/docs/running-collections/intro-to-collection-runs/)

- [Postman Newman (CLI)](https://learning.postman.com/docs/running-collections/using-newman-cli/)