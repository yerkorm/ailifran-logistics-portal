# Transportes Ailifran: Logistics Website and Worker Portal

Live at **[transportesailifran.cl](https://transportesailifran.cl)**

Company website and internal portal for a refrigerated freight company in northern Chile (Antofagasta, Mejillones, Tocopilla, Calama, Taltal).

> Case study. The source code is private because the portal runs in production with the company's operational data.

## What it does

- **Routes:** admins create delivery routes and assign them to drivers; progress is saved on the server, so it survives a phone restart.
- **Routes from photos:** drivers photograph delivery sheets or invoices and the portal extracts the addresses, flagging repeated ones.
- **Daily load from a photo:** the portal reads a photographed loading sheet (product codes and boxes), converts it to kilograms and adds up several sheets without counting the same row twice.
- **Roles** for admins and drivers.

## Technical decisions

- **Document reading with Cloudflare Workers AI.** Row-by-row text extraction instead of a single JSON answer, after the model kept shifting box counts to the neighbouring row. Small screenshots are upscaled in the browser before sending.
- **Cache busting for phones:** a small Python script adds a version fingerprint to JS and CSS before each deploy, so phones never run new HTML with old cached JavaScript.
- **Cloudflare Pages Functions + D1 (SQLite) + KV** for photos; no servers to maintain.

## Stack

HTML / CSS / JavaScript · Cloudflare Pages Functions · D1 · KV · Workers AI · Python (deploy tooling)

Author: Yerko Ramos Molina · Antofagasta, Chile
