# Towards Surgical World-Action Modeling

### A Preliminary Joint Visual-Trajectory Forecasting for Surgical Motion Planning

This repository presents qualitative results for a preliminary surgical world-action model that jointly forecasts future visual states and 2D instrument trajectories. Given five observed surgical frames and trajectory points, it predicts the next fifteen steps.

## Visualization Guide

Each animation shows predictions at **t+3, t+6, t+9, t+12, and t+15**, together with the corresponding trajectories:

- **Blue**: historical input
- **Green**: ground truth
- **Red**: prediction

## Direct One-Shot Prediction

All 15 future visual representations and trajectory points are predicted in one forward pass.

<table>
  <tr>
    <td align="center"><img src="assets/qualitative-results/direct-one-shot/video_43__1_102_2.gif" width="256" alt="Direct one-shot prediction — sample 01"><br><sub>Sample 01</sub></td>
    <td align="center"><img src="assets/qualitative-results/direct-one-shot/video_44__1_102_1.gif" width="256" alt="Direct one-shot prediction — sample 02"><br><sub>Sample 02</sub></td>
    <td align="center"><img src="assets/qualitative-results/direct-one-shot/video_45__1_103_1.gif" width="256" alt="Direct one-shot prediction — sample 03"><br><sub>Sample 03</sub></td>
  </tr>
  <tr>
    <td align="center"><img src="assets/qualitative-results/direct-one-shot/video_45__1_107_1.gif" width="256" alt="Direct one-shot prediction — sample 04"><br><sub>Sample 04</sub></td>
    <td align="center"><img src="assets/qualitative-results/direct-one-shot/video_46__1_102_1.gif" width="256" alt="Direct one-shot prediction — sample 05"><br><sub>Sample 05</sub></td>
    <td align="center"><img src="assets/qualitative-results/direct-one-shot/video_46__1_102_3.gif" width="256" alt="Direct one-shot prediction — sample 06"><br><sub>Sample 06</sub></td>
  </tr>
  <tr>
    <td align="center"><img src="assets/qualitative-results/direct-one-shot/video_46__1_104_6.gif" width="256" alt="Direct one-shot prediction — sample 07"><br><sub>Sample 07</sub></td>
    <td align="center"><img src="assets/qualitative-results/direct-one-shot/video_46__1_108_3.gif" width="256" alt="Direct one-shot prediction — sample 08"><br><sub>Sample 08</sub></td>
    <td align="center"><img src="assets/qualitative-results/direct-one-shot/video_46__1_109_2.gif" width="256" alt="Direct one-shot prediction — sample 09"><br><sub>Sample 09</sub></td>
  </tr>
</table>

## Chunked Autoregressive Rollout

Three future steps are predicted at each stage and recursively reused for the full 15-step rollout.

<table>
  <tr>
    <td align="center"><img src="assets/qualitative-results/chunked-rollout/video_43__1_102_2.gif" width="256" alt="Chunked autoregressive rollout — sample 01"><br><sub>Sample 01</sub></td>
    <td align="center"><img src="assets/qualitative-results/chunked-rollout/video_44__1_102_1.gif" width="256" alt="Chunked autoregressive rollout — sample 02"><br><sub>Sample 02</sub></td>
    <td align="center"><img src="assets/qualitative-results/chunked-rollout/video_45__1_103_1.gif" width="256" alt="Chunked autoregressive rollout — sample 03"><br><sub>Sample 03</sub></td>
  </tr>
  <tr>
    <td align="center"><img src="assets/qualitative-results/chunked-rollout/video_45__1_107_1.gif" width="256" alt="Chunked autoregressive rollout — sample 04"><br><sub>Sample 04</sub></td>
    <td align="center"><img src="assets/qualitative-results/chunked-rollout/video_46__1_102_1.gif" width="256" alt="Chunked autoregressive rollout — sample 05"><br><sub>Sample 05</sub></td>
    <td align="center"><img src="assets/qualitative-results/chunked-rollout/video_46__1_102_3.gif" width="256" alt="Chunked autoregressive rollout — sample 06"><br><sub>Sample 06</sub></td>
  </tr>
  <tr>
    <td align="center"><img src="assets/qualitative-results/chunked-rollout/video_46__1_104_6.gif" width="256" alt="Chunked autoregressive rollout — sample 07"><br><sub>Sample 07</sub></td>
    <td align="center"><img src="assets/qualitative-results/chunked-rollout/video_46__1_108_3.gif" width="256" alt="Chunked autoregressive rollout — sample 08"><br><sub>Sample 08</sub></td>
    <td align="center"><img src="assets/qualitative-results/chunked-rollout/video_46__1_109_2.gif" width="256" alt="Chunked autoregressive rollout — sample 09"><br><sub>Sample 09</sub></td>
  </tr>
</table>

## Observations

Chunked rollout generally preserves operative-scene structure more effectively and produces trajectories closer to ground truth, especially at early and intermediate horizons; both settings show reduced visual fidelity and accumulated trajectory errors at longer horizons.
