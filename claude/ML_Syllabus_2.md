# Machine Learning for Robotics and Industrial Automation
### A 14-Week Undergraduate Course (3rd Year) — Python / scikit-learn / PyTorch

**Main text:** Raschka, Liu & Mirjalili, *Machine Learning with PyTorch and Scikit-Learn* (Packt, 2022). Chapter references (Ch. #, page #) below refer to this book throughout.

---

## Course Philosophy

Every topic is chosen because it has a direct application in robotics or industrial automation: sensor calibration, fault detection, predictive maintenance, visual inspection, time-series prediction, and learning-based control. The course follows the textbook's chapter order closely so students can read ahead, but **trims or compresses topics with limited use in current practice** — bag-of-words NLP, full derivations of historical algorithms, AdaBoost, LDA/t-SNE, GANs, and GNNs are either dropped, folded into a single lecture as a brief pointer, or left as optional reading, freeing time for the material students will actually reach for: gradient boosting, PyTorch fundamentals, CNNs, LSTMs, attention/transformers, and reinforcement learning.

**Prerequisites:** Python fundamentals, linear algebra, probability/statistics, basic control systems.

**Weekly format:** 1 lecture (theory + robotics framing) + 1 lab (hands-on implementation).

---

## Weekly Schedule

### Part 1 — Classical Machine Learning (scikit-learn)

| Week | Topic | Book Chapters | Learning Outcomes | Lab | Robotics / Automation Application |
|---|---|---|---|---|---|
| 1 | ML Foundations & Tooling | Ch. 1 (p.1); Ch. 2 (p.19) — brief recap only | ML taxonomy (supervised/unsupervised/RL); perceptron & Adaline *concept* (not full derivation); Python/NumPy/Pandas refresher; scikit-learn & PyTorch environment setup | Load and visualize real sensor datasets (IMU, force/torque, vibration); train a first perceptron/logistic model | Framing ML as a complement to state estimation and control |
| 2 | Classifiers Tour & Data Preprocessing | Ch. 3 (p.53); Ch. 4 (p.105) | Logistic regression, SVM, decision trees, k-NN; handling missing/categorical data; feature scaling | Classify machine operating states (normal/fault) from sensor features | Multiclass fault detection in industrial equipment |
| 3 | Regression Analysis | Ch. 9 (p.269) | OLS, regularized regression (Ridge/Lasso), polynomial regression, random forest regression | Fit a regression model to calibrate a force sensor / estimate joint friction | Sensor calibration, static system identification |
| 4 | Ensemble Learning | Ch. 7 (p.205) — emphasis on §"Gradient boosting" and XGBoost; AdaBoost covered briefly as historical context only | Bagging, random forests, gradient boosting, XGBoost | Predict remaining-useful-life risk class from vibration/temperature features | Predictive maintenance, root-cause feature importance |
| 5 | Dimensionality Reduction & Clustering | Ch. 5 (p.139) — PCA is the focus, LDA/t-SNE mentioned only briefly; Ch. 10 (p.305) | PCA; k-means, hierarchical clustering, DBSCAN | Cluster machine states from unlabeled vibration spectra; anomaly flagging | Unsupervised anomaly detection when fault labels are unavailable |
| 6 | Model Evaluation & Hyperparameter Tuning | Ch. 6 (p.171) | Pipelines, k-fold cross-validation, learning/validation curves, grid/randomized search, confusion matrix, ROC | **Project Checkpoint 1**: deliver a validated classical ML pipeline on a real dataset | Rigorous evaluation for safety-relevant automation decisions |

### Part 2 — Deep Learning (PyTorch)

| Week | Topic | Book Chapters | Learning Outcomes | Lab | Robotics / Automation Application |
|---|---|---|---|---|---|
| 7 | From Neural Net Foundations to PyTorch | Ch. 11 (p.335) — condensed to core forward/backprop intuition, not the full from-scratch build; Ch. 12 (p.369) | MLP architecture and backpropagation (conceptual); PyTorch tensors, autograd, DataLoader; building/training a first PyTorch model | Re-implement the Week 2 classifier as a PyTorch MLP | Comparing classical vs. neural models on the same fault-detection task |
| 8 | PyTorch Mechanics | Ch. 13 (p.409) | Computation graphs, `nn.Module`, custom layers, loss functions, saving/loading models | Regression project: predict a continuous physical quantity (e.g., robot joint torque / friction residual), following the book's "fuel efficiency" project pattern | Learning-based approximation of nonlinear robot dynamics |
| 9 | Convolutional Neural Networks | Ch. 14 (p.451) | Convolution/pooling, CNN architecture, regularization (dropout, batch norm), building a CNN in `torch.nn` | Train a CNN for visual defect detection on an industrial image set | Automated visual quality inspection on a production line |
| 10 | Recurrent Networks & Sequential Data | Ch. 15 (p.499) | RNN dataflow, vanishing gradients, LSTM cells; building an RNN/LSTM in PyTorch | Forecast a time-series signal (e.g., tool wear, temperature trend) with an LSTM | Predictive maintenance and trajectory/time-series forecasting |
| 11 | Attention & Transformers (concept-level) | Ch. 16 (p.539) — self-attention and the transformer architecture only; BERT/GPT fine-tuning details (§"Fine-tuning a BERT model") skipped as NLP-specific | Why attention outperforms plain RNNs on long sequences; scaled dot-product attention; where transformer-based perception models (e.g., vision transformers, sensor fusion) fit in robotics | Implement scaled dot-product attention from scratch; inspect a pretrained vision transformer | Multi-sensor fusion and modern perception backbones |
| 12 | Reinforcement Learning | Ch. 19 (p.673) | MDPs, value functions, Q-learning, deep Q-learning (DQN) | Solve a grid-world task with Q-learning; extend toward a simple simulated control task | Learning-based control policies for robotic tasks |
| 13 | Deployment & Sim-to-Real | *(synthesis — not a dedicated book chapter)*; brief pointer to Ch. 17 (p.589, GANs) for synthetic training-data generation; brief pointer to Ch. 18 (p.637, GNNs) as further reading for graph-structured problems (e.g., multi-robot systems, kinematic-chain models) | Sim-to-real gap, model export/quantization, latency constraints, inference on embedded hardware, basic ROS integration pattern | Export and benchmark a trained model for real-time inference | Deploying ML models on real robot/PLC-class hardware |
| 14 | Capstone Presentations & Responsible ML | Ch. 19 summary (p.714) as closing framing | Explainability, failure modes, safety considerations, monitoring in production | **Final Project Presentations** | Reflecting on when/why to trust an ML model in a safety-relevant loop |

---

## What Was Cut or Compressed, and Why

- **Ch. 8 (Sentiment Analysis / bag-of-words NLP)** — dropped entirely. It's the book's only fully text-focused chapter, has no natural robotics/automation tie-in, and the bag-of-words approach it teaches has been largely superseded by the transformer-based methods covered (at concept level) in Week 11.
- **Ch. 2 (Perceptron/Adaline from scratch)** — compressed to a short conceptual recap in Week 1 rather than a full derivation-and-implementation pass, since Week 7–8 rebuild the same ideas properly in PyTorch.
- **AdaBoost (part of Ch. 7)** — mentioned as historical context only; gradient boosting and XGBoost get the lab time, since they're what students will actually encounter in predictive-maintenance pipelines today.
- **LDA and t-SNE (part of Ch. 5)** — mentioned briefly; PCA carries the week since it's the dimensionality-reduction tool most used in practice for sensor/vibration data.
- **Ch. 17 (GANs)** and **Ch. 18 (Graph Neural Networks)** — no dedicated weeks. GANs get a one-slide pointer in Week 13 (useful for synthetic defect-image generation when labeled data is scarce); GNNs get a pointer as further reading for students who go on to multi-robot or kinematic-graph problems. Both are interesting but low-yield for a one-semester survey with this program's focus.

This frees roughly 1.5 weeks of contact time compared to following the book chapter-for-chapter, which is why the schedule still closes with a full deployment week (13) and capstone week (14) — the two most directly useful weeks for this audience, and easy to lose if the syllabus just mirrors the table of contents.

---

## Semester Project (runs Weeks 2–14)

Students select one problem tied to a real or simulated robotics/automation dataset:
- Fault detection on a rotating machine (bearing/vibration dataset)
- Visual inspection of manufactured parts
- Predictive maintenance from multivariate sensor time series
- Learning a residual dynamics model for a robotic arm
- A simple RL-based controller in simulation

**Checkpoint 1 (Week 6):** classical ML baseline, properly validated.
**Final delivery (Week 14):** deep learning model compared against the baseline, with a short deployment/feasibility discussion.

---

## Assessment (suggested weighting)

| Component | Weight |
|---|---|
| Lab assignments (weekly) | 30% |
| Project checkpoint (Week 6) | 15% |
| Final project + presentation (Week 14) | 35% |
| Written exam (covers Weeks 1–12 concepts) | 20% |

---

## Tools & Environment

- **Language:** Python 3.x
- **Core libraries:** NumPy, Pandas, Matplotlib
- **Classical ML:** scikit-learn
- **Deep learning:** PyTorch (+ torchvision for the CNN week)
- **Optional:** Gymnasium (formerly OpenAI Gym) for the RL week, matching the book's Ch. 19 examples; ONNX or TorchScript for the deployment week
- **Suggested datasets:** CWRU Bearing Dataset (fault detection), NASA C-MAPSS (predictive maintenance/RUL), a small custom or public defect-inspection image set, IMU/force-torque logs (can be simulated if lab hardware is unavailable)

---

## References

- **Primary text:** Raschka, Liu & Mirjalili, *Machine Learning with PyTorch and Scikit-Learn* (Packt, 2022) — used throughout, chapter mapping above.
- Sutton & Barto, *Reinforcement Learning: An Introduction* — supplementary depth for Week 12, pairs directly with the book's Ch. 19 treatment.
- Selected papers on learning-based control and sim-to-real transfer, assigned as short readings in Weeks 12–13.

---

## Notes for the Instructor

- Weeks 1 and 7 are the two "reset" points — budget extra lab-support time there, since tooling/notation friction (not the math) is usually what slows a controls/robotics cohort down in an ML course.
- If lab access to real hardware is limited, simulated datasets (Gazebo/PyBullet logs, synthetic sensor noise) work fine for Weeks 3–10 and 12; keep at least one real dataset (e.g., CWRU bearings) for the project so students see real noise and label imbalance.
- Week 13 (deployment) has no dedicated book chapter, so plan that lecture's material yourself in advance — it's the week that most differentiates this course from a generic ML survey, and it's the easiest one to lose to schedule slippage.
- The book's chapters 17 and 18 (GANs, GNNs) are left in the reading list as optional extensions for stronger students or those heading toward research projects, without requiring lecture time.
