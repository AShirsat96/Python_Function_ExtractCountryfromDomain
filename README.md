# Domain to Country Lookup

A Python utility that determines the country of origin for a given domain name using IP geolocation. The tool resolves domain names to IP addresses and uses the ipinfo.io API to retrieve country information.

## Prerequisites

- Python 3.8.19
- `requests` library
- Internet connection
- ipinfo.io API access (free tier available)

## Installation

Install the required package:

```bash
pip install requests
```

## Required Libraries
```python
import requests
import socket
```

## Features

### 1. Domain to Country Lookup (Version 1)
```python
def get_country_from_domain(domain_name):
    """
    Resolves a domain name to its corresponding country.
    
    Args:
        domain_name (str): The domain name to lookup (e.g., "www.example.com")
        
    Returns:
        str: Two-letter country code or error message
    
    Example:
        >>> get_country_from_domain("www.pizzahut.com.sg")
        'SG'
    """
```

### 2. Alternative Implementation (Version 2)
```python
def get_Cntry_URL(CoyURL):
    """
    Alternative implementation of domain to country resolution.
    
    Args:
        CoyURL (str): The company URL to lookup
        
    Returns:
        str: Two-letter country code or error message
    
    Example:
        >>> get_Cntry_URL("www.pizzahut.com.sg")
        'SG'
    """
```

## Usage

```python
# Using version 1
domain_name = "www.pizzahut.com.sg"
country = get_country_from_domain(domain_name)
print(country)  # Output: 'SG'

# Using version 2
country = get_Cntry_URL("www.pizzahut.com.sg")
print(country)  # Output: 'SG'
```

## How It Works

1. Domain Resolution:
   - Uses `socket.gethostbyname()` to resolve domain to IP address
   - Handles DNS resolution errors

2. IP Geolocation:
   - Queries ipinfo.io API with resolved IP address
   - Parses JSON response for country information

3. Error Handling:
   - DNS resolution errors
   - API connection issues
   - Missing country information

## API Limitations

- Uses ipinfo.io free tier
- Limited to 50,000 requests per month
- No API key required for basic usage

## Return Values

The functions can return:
- Two-letter country code (e.g., 'SG' for Singapore)
- "Country information not available for this domain"
- Error message with specific exception details

## Error Messages

Common error scenarios:
- DNS resolution failures
- Network connectivity issues
- API rate limiting
- Invalid domain names

## Best Practices

1. Error Handling:
   - Always check return value for error messages
   - Implement rate limiting for bulk queries
   - Handle DNS timeouts appropriately

2. Performance:
   - Cache results for frequently queried domains
   - Implement reasonable timeouts
   - Consider batch processing for multiple domains

3. API Usage:
   - Monitor monthly API usage
   - Consider upgrading to paid tier for higher limits
   - Implement rate limiting to stay within free tier

## Examples

```python
# Successful lookup
result = get_country_from_domain("www.google.com")
print(result)  # Returns country code

# Invalid domain
result = get_country_from_domain("invalid.domain")
print(result)  # Returns error message

# Domain without country info
result = get_country_from_domain("localhost")
print(result)  # Returns "Country information not available"
```
