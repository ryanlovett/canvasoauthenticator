# CanvasOAuthenticator 

CanvasOAuthenticator is a JupyterHub [OAuthenticator](https://github.com/jupyterhub/oauthenticator) that integrates with [Canvas LMS](https://www.instructure.com/canvas) instances. It can also create JupyterHub groups based on Canvas enrollments and groups.

## Configuration

The authenticator is configured through traitlets. Here is an example configuration:

```yaml
c.CanvasOAuthenticator.canvas_url = 'https://bcourses.berkeley.edu/'
c.CanvasOAuthenticator.scope = ['url:GET|/api/v1/users/:user_id/profile, 'url:GET|/api/v1/users/self/groups', 'url:GET|/api/v1/courses']
c.CanvasOAuthenticator.strip_email_domain = 'berkeley.edu'
c.CanvasOAuthenticator.login_service = 'bCourses'
c.CanvasOAuthenticator.username_key = 'primary_email'

C.Authenticator.manage_groups = True
```

Scopes are necessary to retrieve users' usernames, groups, and course information, and your Canvas administrator [will need to enable scoping](https://community.canvaslms.com/t5/Admin-Guide/How-do-I-enable-scoping-for-a-developer-API-key-in-an-account/ta-p/181) for your OAuth developer keys. 
