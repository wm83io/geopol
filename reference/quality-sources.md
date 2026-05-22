## Source-Independence Discipline (added 2026-05-22 via /premortem)

The tier ladder below rates *outlet quality*, not *source independence*. Multi-outlet pickup of the same originating reporter or the same anonymous source cluster is not independent confirmation; it is cluster-laundering. The Day 84 Mojtaba HEU-stays directive was the canonical near-miss: Haaretz lead, Reuters via geo.tv / Al Arabiya / Daily Sabah / Times of Israel — all T2 outlets, all picking up the same "senior Iranian sources" reporting cluster. Five outlets, one source cluster, M confidence at best.

**Provenance rules:**

1. **Originating reporter / outlet identification.** For each multi-source claim, identify the originating reporter and outlet. If all downstream T2 pickups cite the same originating reporter, count as one source for confidence purposes, regardless of outlet count.
2. **Anonymous-source identity.** "Anonymous senior Iranian sources," "two US officials," "senior Israeli officials" are treated as a single source until at least two outlets independently produce distinct named or distinct-cluster anonymous attribution. Multi-outlet pickup of the same anonymous cluster does not satisfy this.
3. **Standing discount on anonymous T2 clusters.** Apply -50% confidence on the originating claim regardless of how many outlets pick it up. The discount mitigates partially on (a) two genuinely independent anonymous clusters reporting the same finding, or (b) at least one named-source corroboration.
4. **Source-cluster log.** Sweeps must record the originating reporter/outlet for each anonymous claim in the `discounts_applied` field. When the same originating cluster appears in 3+ cycles, flag for `/premortem` source-cluster-collapse review.

**Persian-language source priority elevation.** The English-language ladder systematically under-instruments Iranian internal politics. PROBE-3's 14+ consecutive gap cycles is a structural failure surface, not "accept opacity." Where English-language sources are silent on Iranian internal dynamics, attempt Persian-language acquisition via Radio Farda Persian service, IRNA, Tasnim, Fars (read against the grain), and alanchand.com for rial parallel rates before declaring `gap`. Note translation provenance in the finding card.

**Quality-tier coverage for Iranian internal:** Iran International, IranWire, Radio Farda, Persian-language primary sources (IRNA, Tasnim, Fars, alanchand.com), Karim Sadjadpour, Afshon Ostovar. Single-source claims from any one of these still carry -50% discount; cross-source confirmation across exile + diaspora + state-aligned sources required for H confidence.

---

### 1. Kinetic Strategy & OSINT (Nielsen Lens)
- **War on the Rocks**: https://warontherocks.com/
- **Institute for the Study of War (ISW)**: https://www.understandingwar.org/
- **Royal United Services Institute (RUSI)**: https://rusi.org/
- **International Institute for Strategic Studies (IISS)**: https://www.iiss.org/
- **Bellingcat**: https://www.bellingcat.com/
- **Small Wars Journal**: https://smallwarsjournal.com/
- **The Strategy Bridge**: https://thestrategybridge.org/
- **Logic of War**: https://www.logicofwar.com/
- **Mind-War**: https://www.mind-war.com/
- **The War Zone (The Drive)**: https://www.thedrive.com/the-war-zone/

### 2. Structural Power & Realpolitik (Vexler Lens)
- **GZero Media (Ian Bremmer)**: https://www.gzeromedia.com/
- **The Lowy Institute**: https://www.lowyinstitute.org/
- **The Diplomat**: https://thediplomat.com/
- **Carnegie Endowment for International Peace**: https://carnegieendowment.org/
- **Chatham House**: https://www.chathamhouse.org/
- **Quincy Institute (Responsible Statecraft)**: https://quincyinst.org/
- **Foreign Affairs**: https://www.foreignaffairs.com/
- **Foreign Policy**: https://foreignpolicy.com/
- **Lawfare**: https://www.lawfaremedia.org/ — constitutional law and national security; primary venue for WPA/AUMF legal analysis and executive war-powers doctrine
- **One First (Steve Vladeck)**: https://stevevladeck.substack.com/ — national-security law and war powers; Supreme Court and executive authority; essential for constitutional-crisis trajectory (BS-5)
- **Sinocism (Bill Bishop)**: https://sinocism.com/ — China policy synthesis; reads Chinese-language primary sources 24-48h ahead of international press; essential for Xi-Trump summit signal interpretation

### 3. Materialist & Economic Drivers (Marxist Lens)
- **Phenomenal World**: https://www.phenomenalworld.org/
- **The Bourse & Bazaar Foundation**: https://www.bourseandbazaar.org/
- **Energy Intelligence**: https://www.energyintel.com/
- **Naked Capitalism**: https://www.nakedcapitalism.com/
- **The Long View (Michael Roberts)**: https://thenextrecession.wordpress.com/
- **New Left Review**: https://newleftreview.org/

### 4. Economic Base & Market Data
- **Trading Economics**: https://tradingeconomics.com/
- **FT Lex Column**: https://www.ft.com/lex
- **Bloomberg Odd Lots**: https://www.bloomberg.com/podcasts/series/odd-lots
- **SemiAnalysis**: https://www.semianalysis.com/
- **S&P Global Commodity Insights (Platts)**: https://www.spglobal.com/commodityinsights/ — gold standard for oil-flow data and Hormuz throughput modeling; essential for BS-7 energy structural breaks
- **KPLER**: https://www.kpler.com/ — cargo intelligence; Iranian crude export tracking; primary source for export-shipment stall signals
- **Vortexa**: https://www.vortexa.com/ — energy cargo analytics; shadow-fleet and dark-fleet transit monitoring; Hormuz two-track equilibrium quantification

### 5. Tech & Business Strategy (Stratechery Vibe)
- **Stratechery**: https://stratechery.com/
- **Rest of World**: https://restofworld.org/

### 6. Logical & Ethical Foundations
- **Stanford Encyclopedia of Philosophy**: https://plato.stanford.edu/
- **London Review of Books**: https://www.lrb.co.uk/
- **Heather Cox Richardson**: https://heathercoxrichardson.substack.com/

### 7. Israeli Primary Sources
- **Haaretz**: https://www.haaretz.com/ — Israeli investigative daily; essential for IDF institutional dynamics and coalition politics. Key correspondents: Amos Harel (IDF and military affairs — decades of general-staff sourcing), Yossi Melman (intelligence community — Mossad/Shin Bet), Anshel Pfeffer (Netanyahu political-military nexus — biography author)
- **Times of Israel**: https://www.timesofisrael.com/ — establishment Israeli daily; government coalition signals and legal proceedings

### 8. Iran Specialists and Persian-Language Press
- **Iran Wire**: https://iranwire.com/ — exile investigative; civil society, economic-pressure transmission, political prisoner signals; primary source for BS-1b (Iranian political-economic transmission); discount single-source claims 50%
- **Radio Farda (RFE/RL Persian service)**: https://www.radiofarda.com/ — Persian-language broadcast; Iranian internal-politics signal chain; street-level dissent and ethnic-minority indicators
- **Afshon Ostovar — Naval Postgraduate School**: author of *Vanguard of the Imam* (Oxford University Press); the authoritative academic source on IRGC factional structure, Quds Force doctrine, and revolutionary guard political economy. Publishes through IISS, Atlantic Council, and peer-reviewed venues. Primary reference for BS-1a and BS-8 triangle-dynamics questions.
- **Karim Sadjadpour — Carnegie Endowment**: https://carnegieendowment.org/experts/karim-sadjadpour — Iranian elite decision-making, IRGC-clerical dynamics, revolutionary identity as a constraint variable; essential framing for Vahidi apex-opposition modeling

### 9. Russian Investigative
- **Meduza**: https://meduza.io/en — comprehensive Russian internal coverage; Latvia-based independent; essential for siloviki faction dynamics, Shoigu-legal trajectory, and elite-cohesion signals (BS-9 primary source)
- **iStories (Important Stories — OCCRP partner)**: https://istories.media/en/ — broke the EU intelligence dossier on Kremlin coup fears (May 4, 2026); FSB/GRU investigative; corroborated by CNN for BS-9 S3 signal cluster
- **The Insider**: https://theins.ru/en — Russian investigative; complements Meduza on security-service dynamics; strong track record on GRU operational attribution
