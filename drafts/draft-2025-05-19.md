# providers.txt

```txt
Draft: 2025-05-19
Feedback: https://github.com/yuckabug/providers.txt
```

A standardized file that discloses third-party services processing user data on your website.

## Implementation

1. Place at `/.well-known/providers.txt` on your domain root
2. Begin with the **draft** (`Draft`) and your **privacy policy** URL (`Privacy-policy`)
3. List each provider with **required** fields
4. Separate providers with a blank line

## Provider Fields

| Field     | Required | Description                                                 | Values                                           |
| --------- | -------- | ----------------------------------------------------------- | ------------------------------------------------ |
| Name      | Yes      | Provider name                                               | Text                                             |
| URL       | Yes      | Provider website                                            | Valid URL                                        |
| Opt-out   | Yes      | Can users opt out? (with how, if yes)                       | `No` \| Text                                     |
| Purpose   | Yes      | Service function                                            | Text                                             |
| Data      | Yes      | The data access level, what's collected, and if it's shared | Text                                             |
| Location  | No       | Geographic processing regions                               | Text [^1]                                        |
| Retention | No       | Data retention period                                       | `[number]d\|m\|y` \| `Indefinite` \| `None` [^2] |

## Example

```txt
Draft: 2025-05-19
Privacy-policy: https://example.com/privacy

Name: Cloudflare
URL: https://www.cloudflare.com
Opt-out: No
Purpose: CDN and DDoS protection
Data: Reads IP address and request logs, not shared with third parties
Location: US
Retention: None

Name: Google Analytics
URL: https://analytics.google.com
Opt-out: Via cookie banner
Purpose: Website analytics
Data: Reads usage data and device information, not shared with third parties
```

## Acknowledgements

This was inspired by [Christoph Daniel Miksche](https://github.com/CMiksche)'s awesome [network.txt](https://github.com/CMiksche/network.txt).

[^1]:
    While any text is valid, we recommend using
    [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) country codes (e.g., `US,DE,JP`) and/or common
    regions (e.g., `EU`, `APAC`) for consistency and machine readability. However, sometimes something more specific
    is preferable.

[^2]: This can also be represented by the regular expression `^\d+[dmy]$|^(Indefinite|None)$`.
