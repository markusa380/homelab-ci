# homelab-ci

The deploy workflow for the applications on my homelab, shared by their
repositories. It builds a container image, pushes it to the homelab's
private registry over Tailscale, and deploys it by setting the new tag in the
(private) homelab-apps repository, from which Argo CD deploys. Instead of
building the image, it can deploy one that the calling workflow built and
tested (input `image-artifact`).

Usage and inputs: see the comment at the top of
[`.github/workflows/deploy-image.yml`](.github/workflows/deploy-image.yml).

The workflow can only reach the registry when it runs from one of my own
repositories: Tailscale admits exactly this workflow file, from repositories
of `markusa380`, and only to the registry.
