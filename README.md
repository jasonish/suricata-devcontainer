# Suricata Codespace for Developers

## Getting Started

### Using GitHub Codespaces

- Fork this repo
- Open as a codespace on GitHub at https://github.com/codespaces (or see next step)

### Running Locally

- Clone this repo
- Open in Visual Studio Code
- When prompted, "Reopen in Container"

## Build Suricata

Ideally you'd fork the Suricata repo (https://github.com/OISF/suricata) and
clone from there, however for simplicity this instructions assume you have not.
In the DevContainer/Codespace terminal:

1. Change directory into the `src` directory: `cd src`
2. Clone the Suricata repo:
    ```
    git clone https://github.com/OISF/suricata
    ```
3. Change directory into the `suricata` directory: `cd suricata`
4. Bundle in dependencies that are expected to exist:
    ```
    ./scripts/bundle.sh
    ```
5. Build Suricata:
    - `./autogen.sh`
    - `./configure --enable-unittests`
    - `make -j2`
6. Run the unit tests:
    ```
    ./src/suricata -u -l .
    ```
7. Clone and run the Suricata-Verify tests:
    ```
    git clone https://github.com/OISF/suricata-verify ~/src/suricata-verify
    ~/src/suricata-verify/run.py
    ```

## Stop the Codespace

**IMPORTANT**: If running on GitHub Codespaces, stop your codespace when done.
You only get a certain amount of free hours per month.

## Other Notes

If running locally and you use SSH to authenticate against GitHub, you can make
the DevContainer aware of your ssh keys by running the following command on your
machine (not inside the container):

```
ssh-add ~/.ssh/KEY_NAME
```

Replacing `KEY_NAME` with your private key file, usually `id_rsa` or
`id_ed25519`.