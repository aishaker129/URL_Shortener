cat > README.md <<EOL
# URL Shortener Service

A public URL Shortener service built with Spring Boot and MySQL, allowing users to convert long URLs into short, shareable links with validity.

## Features
- Shorten URLs to ≤ 10 characters
- Unique shortened URLs
- Avoid duplicate original URLs
- Expired URLs return "Url expired" message
- Input validation and proper exception handling

## Endpoints
1. POST /api/shorten
2. GET /r/{shortCode}

## Database
Table: short_url
- id (PK)
- original_url (unique)
- short_url (unique, ≤10 chars)
- expiry_date
- create_date

## Error Handling
- 400 Bad Request → Invalid input
- 404 Not Found → URL not found
- 410 Gone → URL expired

## Author
Md. Akhlakul Islam (Shaker)
GitHub: https://github.com/aishaker129
EOL
