🔐 Authentication & Security
Aadhaar Verification Flow
1. User registers with phone number

2. Backend initiates Aadhaar OTP:
   - Sends OTP via SMS
   - User enters OTP
   - Verification API confirms identity

3. Once verified:
   - Aadhaar_verified = true
   - Trust score increases
   - Enables banking features

4. User can now:
   - Get "Verified" badge
   - List crops with authority
   - Access farm loans/insurance
Password Security
- All passwords hashed with bcrypt (salt rounds: 10)
- Never stored in plaintext
- Never transmitted over HTTP (HTTPS enforced)
- Password reset via OTP verification
API Security
- All external API keys stored in environment variables
- Never exposed in frontend code
- Rate limiting: 1000 requests/hour per user
- CORS enabled only for trusted domains

📈 Scalability
Current Capacity

Users: 10,000+ concurrent
Listings: 100,000+ active crops
API Calls: 10,000/minute (data.gov.in + OpenWeatherMap)
Database: Auto-scaling cloud storage

Optimization Strategies

Caching:

Mandi prices cached hourly (not real-time query)
User profiles cached for 5 minutes
Static assets served via CDN


Database Indexing:

Index on (crop_name, state, price_range) for fast filtering
Index on farmer_id for seller queries
Index on created_at for timeline feeds


API Rate Limiting:

data.gov.in: 1000 calls/hour (batched queries)
OpenWeatherMap: 100 calls/minute (cached by city)


Frontend Optimization:

Code splitting by route
Lazy loading of images
Minified CSS/JS bundles
Service Worker for offline support
