# How to Install PECE
1. Clone the project.
2. Copy `.env.example` to `.env`.
3. Update `.env` variables.
4. Run
```shell
$ make up
```
5. Access the admin project and continue the wizard setup.
6. Run
```shell
$ make update
```
7. Setup the [n8n](/n8n/index.md) 

## Build Theme
1. Go to `src/front`
2. Copy `.env.example` to `.env`.
3. Update `.env` variables.
4. Install Simple oAuth and reCAPTCHA
- [Simple oAuth](/auth/oauth.md)
- [Google reCAPTCHA](/auth/recaptcha.md)
5. Run `make install && make build`

## Essencial setups

