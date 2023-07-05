::: mermaid
sequenceDiagram
  participant User as User
  participant Server as Server

  User->>Server: 1. Request Email Verification (メール認証要求)
  Server->>User: 2. Send Verification Code via Email (メール認証コード送信)
  User->>Server: 3. Submit Verification Code (認証コード送信)
  Server->>User: 4. Confirm Verification (認証確認)

  User->>Server: 5. Request Registration (個人会員登録要求)
  Server->>User: 6. Confirm Registration (会員登録確認)

  User->>Server: 7. Login Request (ログイン要求)
  Server->>User: 8. Confirm Login (ログイン確認)

  User->>Server: 9. Request User Information (会員情報要求)
  Server->>User: 10. Return User Information (会員情報返却)

  User->>Server: 11. Request Password Change (パスワード変更要求)
  Server->>User: 12. Confirm Password Change (パスワード変更確認)

  User->>Server: 13. Request Password Reset (パスワード再設定要求)
  Server->>User: 14. Confirm Password Reset (パスワード再設定確認)sequenceDiagram
    participant User as User
    participant API as Server

    User->>API: i. Send email for verification
    API->>User: ii. Send verification code
    User->>API: iii. Enter verification code and personal details for registration
    API->>User: Confirm Registration

    loop Authenticated Actions
        User->>API: vi. Login
        API->>User: Send Auth Token
        opt Need to change password
            User->>API: iv. Change Password
            API->>User: Confirm Password Change
        end
        opt Forgot password
            User->>API: v. Reset Password
            API->>User: Confirm Password Reset
        end
        User->>API: vii. Request Member Info
        API->>User: Return Member Info
    end

  :::
