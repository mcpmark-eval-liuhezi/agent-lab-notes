# Site Dossier — PM2.5 Sensor AQ-PM25-0417 (Beijing)

Prepared for the atmospheric-sensing group. All values below come from live lookups (Google Maps / arXiv / GitHub), keyed off the coordinates in the deployment note — nothing was filled in from memory.

## 1. Site

- **Sensor ID:** AQ-PM25-0417
- **Coordinates (from note):** 39.904211, 116.407395 (WGS84, decimal degrees)
- **City resolved:** Beijing, China
- **City Google place ID:** ChIJuSwU55ZS8DURiqkPryBWYrk
- **Ground elevation at sensor:** 45.25 m (45.24945449829102 m, Google Elevation API)
- **Reverse-geocoded address:** 2 Zheng Yi Lu, Dong Cheng Qu, Bei Jing Shi, China, 100051
- **Mounting:** rooftop mast, ~15 m above ground (per note) → inlet approx. 60.25 m ASL
- **Installed:** 2026-09-30 (per note)

Notes on the city lookup: the coordinate reverse-geocode returns the Dongcheng District address above; the locality-level Google place record for those coordinates is "Beijing, China" with the place ID listed. Sensor ID and mounting details are copied verbatim from deployment_note.txt.

## 2. Nearby institutions (three closest)

Candidates were collected with Google Places text/radius searches around the site, then ranked by great-circle distance from the sensor. The three nearest genuine universities / research institutions are:

1. **Chinese Academy of Medical Sciences** — 9 Dong Dan San Tiao, Dong Cheng Qu, Bei Jing Shi, China, 100006 — one-way driving 2.8 km (2811 m), 11 mins (674 s)
2. **Chinese Academy of Social Sciences** — 5 Jian Nei Da Jie, Dong Cheng Qu, Bei Jing Shi, China, 100005 — one-way driving 3.3 km (3345 m), 9 mins (539 s)
3. **China Foreign Affairs University** — 24 Zhan Lan Guan Lu, Xi Cheng Qu, Bei Jing Shi, China, 100044 — one-way driving 9.4 km (9361 m), 25 mins (1474 s)

### Averages (computed, not mental math)

Command run:

```
python -c "exec('ds=[2811,3345,9361]\nts=[674,539,1474]\nprint(\"driving distances (m):\",ds)\nprint(\"driving durations (s):\",ts)\nprint(\"avg distance (m):\",sum(ds)/len(ds))\nprint(\"avg distance (km):\",sum(ds)/len(ds)/1000)\nprint(\"avg duration (s):\",sum(ts)/len(ts))\nprint(\"avg duration (min):\",sum(ts)/len(ts)/60)')"
```

Exact output:

```
driving distances (m): [2811, 3345, 9361]
driving durations (s): [674, 539, 1474]
avg distance (m): 5172.333333333333
avg distance (km): 5.1723333333333334
avg duration (s): 895.6666666666666
avg duration (min): 14.927777777777777
```

- **Average one-way driving distance: ~5.17 km (5172.33 m)**
- **Average one-way driving duration: ~14.93 minutes (895.67 s, about 14 min 56 s)**

Method note: the shell available in the workspace rejects multi-line `python -c` strings, so the arithmetic was wrapped in exec() with backslash-n line breaks — that is the single command shown above, pasted verbatim.

### Walking route to the closest institution

Closest of the three by both straight-line and driving distance: **Chinese Academy of Medical Sciences** (9 Dong Dan San Tiao).

- **Total walking distance: 1.4 km (1433 m)**
- **Total walking time: 26 mins (1583 s)**
- **Route (main road):** 正义路 (Zheng Yi Lu) → 南河沿大街 → 霞公府街 → 大纱帽胡同 → 东单三条, destination on the left

Step breakdown returned by the routing API: 422 m (10 min) north on 正义路, 185 m (4 min) on 南河沿大街, 52 m (1 min) right onto 霞公府街, 132 m (2 min) right to stay on 霞公府街, 135 m (2 min) left toward 大纱帽胡同, 214 m (3 min) right onto 大纱帽胡同, then 293 m (4 min) onto 东单三条.

## 3. Monitoring context

Nearest official air-quality / environmental monitoring facility found near the site:

- **Name:** Beijing Environmental Protection Monitoring Center
- **Address (as returned):** China, Bei Jing Shi, Hai Dian Qu, 车公庄西路14号 邮政编码: 100089 (14 Che Gong Zhuang Xi Lu, Haidian District, Beijing)
- **Phone (as returned):** 010 6845 6814
- **Website (as returned):** http://www.bjmemc.com.cn/
- **Google place ID:** ChIJ5wfRGopR8DURHlKxWeDfONE

Other nearby facilities returned by the same lookups, for reference: Beijing Environmental Protection Bureau (14 Che Gong Zhuang Xi Lu, Haidian District, 100089) and Beijing Climate Center (46 Zhong Guan Cun Nan Da Jie, Haidian District, 100082).

## 4. Literature (arXiv mirror)

Searched the arXiv mirror for air-quality / particulate-pollution work tied to Beijing. The city-specific query already returned a solid set, so no broadening was needed. The five strongest, exactly as returned by the search:

1. **Same-Hour Estimation and Multi-Horizon Forecasting of PM2.5 in Beijing: Model Comparison and Feature-Group Contributions** — Yusheng Wang (2026)
2. **Natural gas shortages during the "coal-to-gas" transition in China have caused a large redistribution of air pollution** — Siwen Wang (2020)
3. **A Novel Hybrid Framework for Hourly PM2.5 Concentration Forecasting Using CEEMDAN and Deep Temporal Convolutional Neural Network** — Fuxin Jiang (2020)
4. **Significant reduced traffic in Beijing failed to relieve haze pollution during the COVID-19 lockdown: implications for haze mitigation** — Zhaofeng Lv (2020)
5. **Deep Inferential Spatial-Temporal Network for Forecasting Air Pollution Concentrations** — Hao Wang (2018)

Relevance notes (from the returned abstracts):
- #1 uses 420,768 hourly observations from 12 monitoring stations in Beijing, 2013–2017.
- #3 validates on Beijing PM2.5 concentration data.
- #5 evaluates on 35 Beijing monitoring stations plus grid meteorology.
- #2 and #4 are Beijing / northern-China air-pollution attribution studies.

## 5. Code and data

Searched GitHub for open-source code/datasets tied to Beijing air quality or PM2.5. A healthy number of city-specific repos exist (Beijing PM2.5 prediction projects, KDD Cup 2018 Beijing/London air-quality solutions, and the classic UCI "Beijing PM2.5" / PRSA dataset that several repos ship). The single most relevant pick:

- **Repository:** DojoZheng/AirQualityPrediction
- **One-line description:** Jupyter-notebook project applying machine-learning techniques to analyse and predict air quality in Beijing.
- **Most recent commit SHA:** ff73da2a0f1cfebcf2bb556fe60c1f7b46efedeb
- **Most recent commit — author:** DojoZheng (zhengdongjia@foxmail.com)
- **Most recent commit — date:** 2019-02-28T13:00:22Z
- **Most recent commit — message:** "Upload the files of the project"

The connection is **direct and city-specific**, not indirect: the repository is explicitly a Beijing air-quality analysis/prediction project (37 stars, 15 forks at time of lookup).

## 6. Loop-in list (organization teams)

Checked the authenticated account (HeziLiu):

- The account **belongs to one organization**: mcpmark-eval-liuhezi.
- That organization contains **no teams that the account is a member of** — the teams listing for the account came back empty.
- Therefore there are **no team member usernames to list**; there is nobody to loop in via an org team for this dossier.

Stated plainly: no organization teams were found, so no loop-in list exists.

## 7. Housekeeping (dangling pull request reviews)

Checked for pending (unsubmitted, half-finished) pull request reviews associated with the account. The org has a large number of sandbox/demo pull requests, many of them explicitly built as "review drill" or "smoke test" PRs for exercising the pending-review flow, so every review-related PR was probed with the discard-pending-review call.

Result: **no pending review was found anywhere.** Every probe returned "No pending review found for the viewer", and the handful of PRs that do carry a review from this account already have that review **submitted** (state COMMENTED), not pending — for example the review on the weekend-visit-plan PR is a submitted comment review, not a dangling draft.

Stated plainly: there are no half-finished pending PR reviews to discard, so nothing was deleted and nothing half-baked can slip out.

End of dossier. Generated from deployment_note.txt (sensor ID AQ-PM25-0417) plus live Google Maps, arXiv and GitHub lookups.
