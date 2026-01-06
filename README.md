# official
# TOKOA — Design System & Spécifications (résumé)

## Concept
TOKOA est une app de transfert/réception d’argent internationale au design minimaliste, moderne, privilégiant clarté et confiance. L’esthétique : "liquid glass" (glassmorphism) — surfaces translucides, flous, dégradés doux, micro-animations liquides pour apporter dynamisme sans surcharge.

## Palette (minimaliste)
- Background clair principal : #F7F8FA
- Background sombre (mode sombre) : #0B1020
- Accent principal (teal) : #2DD4BF
- Accent secondaire (indigo doux) : #7C5CFF
- Glass (clair) rgba(255,255,255,0.12)
- Glass (sombre) rgba(12,14,21,0.24)
- Texte principal (clair) : #0B1020
- Texte principal (sombre) : #F7F8FA
- Succès : #16A34A
- Erreur : #EF4444

Dégradé liquide d’accent :
- gradientStart: rgba(124,92,255,0.18) (#7C5CFF @ 18%)
- gradientEnd: rgba(45,212,191,0.12) (#2DD4BF @ 12%)

## Typographie
- Police iOS recommandée: San Francisco (SF Pro Display / SF Pro Text)
- Titres: SF Pro Display, weights 600–700
- Corps: SF Pro Text, weights 400–600
- Intervalles de base: small 12, body 16, large 20–34

## Layout & composants
- Card radius: 16pt (éléments principaux), 10pt (mini-cards)
- Shadow (subtil): y: 8, blur: 20, color: rgba(11,16,32,0.12)
- Spacing scale: 8 / 12 / 16 / 24 / 32 / 48
- Buttons: hauteur 52pt (CTA principal), pill shape (corner 26pt), fond accent avec léger glass overlay

## Glassmorphism / Liquid glass
- Utiliser Material (.ultraThinMaterial / .regularMaterial) pour iOS 15+
- Couche principale : fond translucide + blur (UIVisualEffectView)
- Overlay de dégradé léger pour effet liquide
- Ajout de blobs colorés flous, animés lentement (translation/scale/opacity)
- Bords: stroke blanc 8% opacity + inner highlight

## UI Flow (écrans clés)
1. Splash animé (logo liquide)
2. Onboarding (3 cartes) — expliquer frais, rapidité, sécurité
3. Auth: email/phone + biométrie
4. KYC progress (upload docs)
5. Dashboard: solde(s) multi-devises, actions rapides Send / Receive
6. Send flow: destinataire (contact ou IBAN), montant, conversion, fees, confirmation + OTP
7. Receive flow: code QR / lien, détails de retrait local
8. Transactions: timeline + filtering
9. Contact management
10. Settings: security, languages, support, limits

## Accessibilité & Internationalisation
- Localisation FR / EN + autres (RTL si besoin)
- Contraste pour textes (AA min), tailles dynamiques, VoiceOver labels
- Utiliser couleurs non seules pour états (icônes + texte)

## Sécurité & Conformité
- Chiffrement côté client (Keychain pour tokens)
- TLS 1.2+, HSTS
- KYC & AML flows selon juridiction
- PCI-DSS pour paiements par cartes
- Stockage minimal côté appareil (token & prefs)

## Backend & rails recommandés
- Backend: API REST/GraphQL, Webhooks pour statuts
- Intégrations: SWIFT / SEPA / ACH / local payout partners / mobile money (selon pays)
- Provider de change (fixer-rates + streaming rates), sandbox rates
- Monitoring & SRE: Sentry, Datadog, Prometheus

## Animation & micro-interactions
- Durées lentes et organiques: 600–1200ms pour blobs; 200–350ms pour boutons
- Haptics: succès/tap/long-press
- Microcopy clair: frais affichés avant confirmation

## Iconographie & logo
- Minimal, symbole évoquant échange / pont (deux flèches stylisées ou deux formes superposées)
- Palette translucide, calque de dégradé à l’intérieur de l’icône
- Format icône: 1024×1024, bord arrondi adaptatif

## Livrables recommandés
- Figma file with components & variants (light/dark)
- Tokens JSON, assets (SVG/PNG), SwiftUI components
- Prototype interactif (onboarding + send flow)
