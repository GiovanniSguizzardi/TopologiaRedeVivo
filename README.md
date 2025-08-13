# Topologia de Rede – Instruções do Projeto (Packet Tracer)

Este repositório contém a **topologia de redes** construída no **Cisco Packet Tracer** para representar parte da rede de comunicação da empresa parceira.

## 🎯 Objetivo
Criar uma topologia no Packet Tracer com **identificação dos elementos de conectividade** (Switches, Roteadores e Access Points), usando um **endereço IPv4 Classe C público** como ponto de partida, subdividido via **CIDR/VLSM**.

---

## 🧩 Requisitos Mínimos da Topologia
1. **Nuvem** representando a **Internet**.  
2. **Roteador de borda** conectando a empresa à Internet.  
3. **Três segmentos LAN** (3 **sub-redes**) conectadas ao roteador, obtidas por **CIDR/VLSM** a partir do bloco Classe C escolhido.  
4. **DHCP (IPv4)** ativo para alocação automática de endereços dos hosts.  
5. **Anotações visíveis no diagrama** contendo:
   - Bloco **IPv4 Classe C** escolhido  
   - **Máscara/CIDR** de cada sub-rede  
   - **Faixa de hosts** utilizada em cada segmento  
6. **IPv6 habilitado** em todos os dispositivos (prefixos por LAN).  
7. **Servidor HTTP** com uma página exibindo os **nomes dos integrantes da equipe**.  
8. **Servidor DNS (IPv4 e IPv6)** resolvendo **`www.fiap.com.br`** para o servidor HTTP (registros **A** e **AAAA**).  

---

## 🗺️ Planejamento de Endereçamento (preencha)
**Bloco IPv4 Classe C:** `<ex.: 203.0.113.0/24>`  

| LAN | Rede (CIDR) | Máscara | Gateway | Pool DHCP (início–fim) |
|-----|-------------|---------|---------|-------------------------|
| A   | `<ex.: 203.0.113.0/26>`  | `255.255.255.192` | `<.1>` | `<.10 – .62>` |
| B   | `<ex.: 203.0.113.64/27>` | `255.255.255.224` | `<.65>`| `<.70 – .94>` |
| C   | `<ex.: 203.0.113.96/28>` | `255.255.255.240` | `<.97>`| `<.100 – .110>` |

**Plano IPv6 (exemplo de /48 → /64 por LAN):**  
Prefixo global: `<ex.: 2001:db8:abcd::/48>`

- LAN A: `2001:db8:abcd:1::/64`  
- LAN B: `2001:db8:abcd:2::/64`  
- LAN C: `2001:db8:abcd:3::/64`

---

## 🏷️ Padrão de Nomes dos Elementos
- **Roteador:** `R1`  
- **Switches:** `SW-A`, `SW-B`, `SW-C`  
- **Access Point:** `AP-1` (em uma das LANs)  
- **Servidores:** `S1-HTTP`, `S2-DNS`  
- **Hosts:** `PC-A1..A<n>`, `PC-B1..B<n>`, `PC-C1..C<n>`

---

## ⚙️ Serviços / Configuração Esperada
- **DHCP (IPv4)**: 1 pool por LAN (gateway + dns-server apontando para `S2-DNS`).  
- **IPv6**: SLAAC e/ou DHCPv6 por LAN (com DNSv6 apontando para `S2-DNS`).  
- **HTTP (S1-HTTP)**: página `index.html` com os nomes da equipe.  
- **DNS (S2-DNS)**:  
  - Registro **A** → `www.fiap.com.br` → IPv4 do `S1-HTTP`  
  - Registro **AAAA** → `www.fiap.com.br` → IPv6 do `S1-HTTP`

---

## ✅ Critérios de Aceite / Testes
- **Conectividade IPv4 e IPv6** entre hosts de LANs diferentes (uso do `ping`).  
- Resolução de nome **`www.fiap.com.br`** em **IPv4 e IPv6** (DNS OK).  
- Acesso via navegador à página do **HTTP Server** com os **nomes da equipe**.  
- **Anotações na topologia** contendo bloco Classe C, máscaras e faixas de hosts.

---

## 📦 Entrega
- Arquivo do Packet Tracer: **`.pkt`** totalmente **configurado**.  
- Compactar em **`.zip`** para submissão.  
- Recomenda-se incluir um **README curto** e, opcionalmente, uma **imagem do diagrama**.

---
