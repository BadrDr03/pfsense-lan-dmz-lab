# Evidence index

Real screenshots copied without alteration from the lab walkthrough. Diagrams are explanations, not test evidence. No synthetic terminal or firewall screenshots are used.

## LAN HTTP 200 and blocked ping

Capture: `20261029-163528`.

![LAN HTTP 200 and blocked ping](../assets/lan-http-ping.png)

## LAN rule matching the ICMP blocks

Capture: `20261029-163943`.

![LAN rule matching the ICMP blocks](../assets/lan-block-logs.png)

## Successful DNS resolution

Capture: `20261029-151307`.

![Successful DNS resolution](../assets/dns-success.png)

## DMZ-to-LAN ICMP blocks

Capture: `20261101-153119`.

![DMZ-to-LAN ICMP blocks](../assets/dmz-lan-block-logs.png)

## Timeout reaching firewall HTTPS

Capture: `20261101-153411`.

![Timeout reaching firewall HTTPS](../assets/dmz-firewall-timeout.png)

## Firewall-self rule blocking TCP SYN

Capture: `20261101-153645`.

![Firewall-self rule blocking TCP SYN](../assets/dmz-firewall-block-logs.png)

## SSH active, enabled and listening on 22

Capture: `20261101-162916`.

![SSH active, enabled and listening on 22](../assets/ssh-service.png)

## LAN rules saved, before Apply Changes

Capture: `20261101-163557`.

![LAN rules saved, before Apply Changes](../assets/lan-rules-ssh.png)

## Nginx configuration test successful

Capture: `20261101-164659`.

![Nginx configuration test successful](../assets/nginx-config-success.png)

## Automatic NAT for LAN and DMZ

Capture: `20261101-165031`.

![Automatic NAT for LAN and DMZ](../assets/outbound-nat.png)

## Final applied DMZ policy

Capture: `20261101-165228`.

![Final applied DMZ policy](../assets/dmz-rules-final.png)

## Nginx active/enabled

Capture: `20261029-155207`.

![Nginx active/enabled](../assets/nginx-service.png)

## Local HTTP 200

Capture: `20261029-155333`.

![Local HTTP 200](../assets/nginx-local-http.png)

## Earlier installation evidence

- [Ubuntu installation](../assets/ubuntu-installed.png)
- [Ubuntu IP and route](../assets/ubuntu-network.png)
- [Initial mirror DNS failure](../assets/mirror-dns-failure.png)

The original `architecture.png` and `traffic-policy.png` are historical illustrations from the infrastructure checkpoint; the latter describes a then-planned policy. Use the current README and final policy tables instead.

HTTPS 200 with `--cacert`, SSH login, and outbound HTTPS 200 were confirmed by the operator in text. Their exact successful output was not supplied as an image and has not been fabricated. The LAN SSH rule image retains its pending-apply banner; the later login confirmation is separate evidence.
