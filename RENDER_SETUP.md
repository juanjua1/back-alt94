# Render.com deployment settings

# Build settings
build:
  - npm install
  - npm run build

# Runtime settings
start: npm run start:prod

# Health check
health_check: /

# Environment variables (set these in Render dashboard)
# MONGODB_URI: Your MongoDB Atlas connection string
# JWT_SECRET: Your JWT secret key
# JWT_EXPIRES_IN: 1d
# NODE_ENV: production
# CORS_ORIGIN: https://your-frontend-domain.vercel.app
