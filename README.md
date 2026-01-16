# Peether Settlement Protocol

**The open-source settlement infrastructure for ride-hailing networks.**

Peether enables any ride-hailing platform to:
- Pay drivers in PTDT (Pink Taxi Drive Token)
- Convert PTDT to local fiat (on-demand)
- Operate independently (no central authority)
- Scale globally (one codebase, infinite deployments)

## What Is Peether?

Think of Peether like **Stripe for ride-hailing**, but:
- Built on blockchain (no centralized payment processor)
- Open-source (anyone can deploy)
- Decentralized (no single point of failure)
- Composable (integrate your own payment processors)

## How It Works

**Layer 1 (Blockchain):** PTDT smart contracts on BSC
**Layer 2 (API):** Peether Settlement Protocol (this repo)
**Layer 3 (Operations):** Your local Pink Taxi deployment

You deploy Layer 2, integrate with Layer 1, operate Layer 3.

## Who Is Using This?

- 🇵🇰 Pink Taxi Pakistan (first deployment)
- 🇳🇬 Pink Taxi Nigeria (planning deployment)
- 🇧🇷 Pink Taxi Brazil (planning deployment)
- [Your operator here] (fork this repo, customize, deploy)

## Getting Started

1. Fork this repo
2. Copy `operator.config.template.ts` → `operator.config.ts`
3. Fill in YOUR operator details
4. Choose YOUR fiat adapter (JazzCash, Flutterwave, Pix, custom)
5. Deploy to YOUR servers
6. Integrate with YOUR app
7. Your drivers earn PTDT

## Documentation

- [Protocol Overview](./docs/PROTOCOL-OVERVIEW.md)
- [Integration Guide](./docs/SETTLEMENT-API.md)
- [Operator Guide](./docs/OPERATOR-GUIDE.md)
- [Deployment](./docs/DEPLOYMENT-GUIDE.md)
- [Compliance](./docs/COMPLIANCE-GUIDE.md)

## License

MIT - Use freely, modify, deploy wherever you want.

## Support

- GitHub Issues for bugs
- GitHub Discussions for questions
- Community Discord for support

---

**Peether: Because ride-hailing drivers deserve global, decentralized compensation.**
