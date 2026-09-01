# Tərcümə Qeydləri — Translation Notes

*Bu fayl Azərbaycan dilinə tərcümənin insan əli və ya qərarla toxunulmuş
hər ayəsini göstərir. Qalan qeydlər ingiliscədir — İbrani mətninin quruluşu
və istinadlar haqqındadır.*

This file records every verse where a human hand or a ruling touched the
Azerbaijani rendering — the fifty-first chair, the first Turkic chair — so
any verse can be audited: machine-pressed under the rails, hand-rendered, or
ruled, and why. Rails: the Selah Azerbaijani discipline (Yahve / Elohim at the
Name seat; ⟨את⟩ total; ⟨…⟩ marks supplied words only; Şeol never *Cəhənnəm*;
Məsih never *İsa* / *Xristos*; Rəbb / Yehova / Allah·Tanrı at the Name seat
rejected).

## The burn and the gleaning (2026-09-01)

The altar-fire relay rendered the corpus in one pass and a retry (lit 05:45,
moved on 13:52) with **73 residue** verses, pressed one per call. The census
flagged content faults and every flagged verse was deleted and re-rendered
through the rails, round by round: **470 → 30 → 8**. The eight that survived
three renders were repaired by hand (below). Final census: Yahve 5,771 ·
Elohim 2,075 · ⟨את⟩ in 7,304 verses · every leak class zero.

## A census gap found and closed

The clone's Name-seat regex looked for *Yehova* and missed the Azerbaijani
spelling **Yəhova** (ə). Found by the token-level Rəbb check (Jer 11:22);
`az_census.clj` / `az_gleaning.clj` now match both. Word boundaries in these
scripts use Unicode classes (`(?U)`) — Java's default `\b` is ASCII-only and
fails next to ə / ı / ş.

## Hand-repaired verses (2026-09-01)

Scripts in the Selah repo hold every pair: `dev/scripts/az_hand_fixes.clj`
(passes 1–3).

- **Cyrillic а inside Latin words** — *2 Sam 1:14* onа; *Deut 11:6* Aviramа;
  *Deut 25:9* adamа; *Lev 17:16* yumasа ×2 → Latin a.
- **Marker glyph corrupted** — *Exod 35:11* ⟨את]] ×3 → ⟨את⟩ (glyph only), and
  a junk word for קרסיו → **qarmaqlarını**.
- **Translator note in ascii brackets** — *Deut 22:13* `<(yəni nifrət etsə)>`
  dropped.
- **Raw Hebrew in a fill** — *Ezek 43:4* ⟨אל⟩ dropped.
- **English article beside a true marker** — *2 Sam 1:17* ⟨את⟩ ⟨the⟩ → ⟨את⟩
  (the marker kept, the article dropped).
- **The Name** — *Jer 11:22* Yəhova → **Yahve**; "Lord of hosts" fills
  (*Jer 11:22*, *Jer 20:12*) → **Yahve Şəbaut**; *Zech 2:13* the parenthetical
  (əsgərlərin Rəbbi) dropped.
- **Allah / Tanrı at true-God seats and in fills** → the rails' forms: *Gen
  22:3* Allahın → **Elohimin**; *Exod 17:9* → **Elohimin əsası**; *Job 20:29*
  Allahdan → **Elohimdən**; *Hos 4:12* Allahlarını → **Elohimlərini**; fills
  ⟨Allah⟩/⟨Allahı⟩/⟨Allaha⟩/⟨Allahım⟩ → ⟨Elohim…⟩ in *Ps 10:4, 70:2, 136:10*,
  *Exod 34:6*, *Jer 20:12*; *Gen 18:29* ⟨Allah⟩ → ⟨o⟩; *Ps 68:33* a wrong
  ⟨tanrılarının⟩ fill dropped.
- **The Rəbb floor** — *Gen 19:19* נא glossed *rəbbim (yumuşaldıcı)* → **indi**;
  *Jer 51:8* a garbled gloss for צרי → **məlhəm**.
- **Aleph-tav unresolved (glyph on a non-marker word)** — *Gen 39:9* and *Prov
  7:4* את the PRONOUN (H859) → **sən**; *Dan 3:12* Aramaic יתהון → **onları**;
  *Ezek 43:23* מחטא → **günahdan**; *Ps 50:1* a phantom marker (the verse has
  none) removed.
- **Token surgery** — *1 Sam 1:10* ובכה תבכה had been merged into one token
  (7 vs the graph's 8): split to **ağlaya / ağladı**.
- **Re-rendered** (empty or misaligned after two renders) — *SoS 2:7* and the
  52 aleph-tav-misaligned verses.

## Per-token review — the Allah/Tanrı and Rəbb floors (2026-09-01)

- **Allah / Tanrı**: 169 verses after the burn. Read per token against the
  Hebrew seat (`dev/scripts/az_tekoa_fixes.clj`, mapping by the corpus's own
  Elohim morphology — *Elohimin* 341×, *Elohimi* 240×, *Elohimimiz* 79× …):
  **4** capital forms on an אלהים-family surface → **Elohim + suffix** (2 Kgs
  7:17–19, Neh 7:5); **159 lawful** (lowercase *tanrı / tanrılar / tanrıları* —
  the gods of the nations, idol seats; kept); the rest by hand (above). Two
  lawful lowercase fills remain (*Deut 32:17* ⟨tanrılara⟩, *Isa 43:12* ⟨tanrı⟩).
- **Rəbb**: token-level against the surfaces: **יהוה → Rəbb: 0**. The 3
  remaining are the place-name Rabbah (Amos 1:14, Josh 13:25) and a human
  אדני (1 Kgs 1:31 *Rəbbim*).

## Aleph-tav audit (2026-09-01)

Graph H853/H854 indices are the truth (`lang_aleph_tav_audit.clj`, `audit :az`
→ `repair! :az`). First pass: 5 stray glyphs stripped, 4 sentences edited,
0 missing, **52 misaligned** → re-rendered; 5 glyph-only glosses for the hand
(above). Second pass: 1 misaligned → token surgery. Final: **misaligned 0 ·
stray 0 · missing 0**.

## Tooling issues met on this chair

- Every language literal in the cloned census / gleaner / Tekoa was fixed
  before the first run (the Somali lesson); one still slipped — the ə in
  Yəhova. Check the target's orthographic variants of every rejected form.
- Azerbaijani words *an*, *on*, *it* collide with the English fill stoplist and
  were removed from it.
- Java regex `\b` is ASCII-only: use `(?U)` for any boundary next to ə ı ö ü ç ş.

## Open for Scott

- UI catalog flags (`docs/language/stragglers/az.md`, 30): *Tövrat* vs *Tora*;
  **HOŞEN** / *sinəbənd*; **YHVH** (no *w* in Azerbaijani); *lif* for fiber;
  *dənə*; *kürsü* for both lectern and chair.
- Whether the *Lord of hosts* fills should read **Yahve Şəbaut** (as here) or
  **Yahve Tsevaot**.
