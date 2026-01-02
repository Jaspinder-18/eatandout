# Troubleshooting Guide

## Fixed Issues

### 1. Contact Form Errors
**Problem**: Validation errors not displaying properly
**Solution**: 
- Added better error handling in frontend
- Backend now returns both `message` and `errors` array
- Added console logging for debugging

### 2. Menu Item Creation Errors
**Problem**: FormData not being sent correctly, boolean values not handled
**Solution**:
- Fixed API interceptor to not set Content-Type for FormData
- Properly convert booleans to strings before sending
- Added validation and better error messages
- Created uploads directory

## How to Debug

### Check Browser Console
1. Open browser DevTools (F12)
2. Go to Console tab
3. Look for error messages when submitting forms
4. Check Network tab to see API requests/responses

### Check Server Logs
The server now logs:
- Received form data
- Validation errors
- File uploads
- Success/failure messages

### Common Issues

#### 1. "Missing required fields" error
- **Cause**: Form fields not filled
- **Fix**: Fill all required fields (name, description, price, category)

#### 2. "Access denied" or 401 error
- **Cause**: Not logged in or token expired
- **Fix**: Log in again at `/admin/login`

#### 3. Image upload fails
- **Cause**: File too large or wrong format
- **Fix**: Use images under 5MB, formats: jpg, png, webp

#### 4. Contact form validation error
- **Cause**: Invalid email or empty fields
- **Fix**: Check email format and fill all fields

## Testing Steps

### Test Contact Form:
1. Go to http://localhost:3000/contact
2. Fill all fields
3. Submit form
4. Check browser console for any errors
5. Check server terminal for logs

### Test Menu Item Creation:
1. Login at http://localhost:3000/admin/login
2. Go to Menu Items tab
3. Click "Add New Item"
4. Fill form:
   - Name: Test Item
   - Description: Test description
   - Price: 100
   - Category: Punjabi
   - (Optional) Upload image
5. Check "Available" checkbox
6. Submit
7. Check browser console and server logs

## Server Logs to Watch For

### Successful Menu Item Creation:
```
Received menu item data: { name: '...', price: '...', ... }
File received: menu-1234567890-123456789.jpg (or No file)
Menu item saved successfully: [objectId]
```

### Successful Contact Form:
```
Received contact form data: { name: '...', email: '...', ... }
Contact message saved successfully: [objectId]
```

### Errors:
- Check for validation errors
- Check for database connection errors
- Check for file upload errors

## If Still Having Issues

1. **Clear browser cache** and reload
2. **Check MongoDB is running**: `mongod` or check service
3. **Restart servers**: Stop and restart both backend and frontend
4. **Check .env file**: Ensure all variables are set correctly
5. **Check file permissions**: Ensure uploads directory is writable

## Contact Form Error Messages

- "Name is required" - Name field is empty
- "Please provide a valid email" - Email format is invalid
- "Phone number is required" - Phone field is empty
- "Message is required" - Message field is empty

## Menu Item Error Messages

- "Missing required fields" - One or more required fields are empty
- "Failed to create menu item" - Check server logs for details
- "Access denied" - Not logged in, login again

