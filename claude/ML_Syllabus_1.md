# Machine Learning for Robotics and Industrial Automation
### A 14-Week Undergraduate Course (3rd Year) — Python / scikit-learn / PyTorch

---

## Course Philosophy

This course does not attempt to cover machine learning broadly. Every topic is chosen because it has a direct, demonstrable application in robotics or industrial automation: sensor calibration, fault detection, predictive maintenance, visual inspection, trajectory/time-series prediction, and learning-based control. Classical ML (weeks 1–7) uses **scikit-learn**; deep learning (weeks 8–14) uses **PyTorch**. A single semester-long project runs in parallel with the lectures, with a checkpoint at Week 7 and final delivery at Week 14.

**Prerequisites:** Python fundamentals, linear algebra, probability/statistics, basic control systems.

**Weekly format:** 1 lecture (theory + robotics framing) + 1 lab (hands-on implementation).

---

## Weekly Schedule

### Part 1 — Classical Machine Learning (scikit-learn)

| Week | Topic | Learning Outcomes | Lab | Robotics / Automation Application |
|---|---|---|---|---|
| 1 | Introduction to ML for Automation | ML taxonomy (supervised/unsupervised/reinforcement); when to use ML vs. classical control/estimation; Python/NumPy/Pandas refresher; scikit-learn & PyTorch environment setup | Load and visualize real sensor datasets (IMU, force/torque, vibration) | Framing ML as a complement to state estimation and control |
| 2 | Data Pipelines & Signal Preprocessing | Handling missing/noisy data; normalization/standardization; feature engineering from time-series signals; train/test/validation splits | Build a preprocessing pipeline for noisy encoder/IMU data | Sensor data cleaning before use in estimation or diagnostics |
| 3 | Linear & Polynomial Regression, Regularization | OLS, Ridge, Lasso; bias-variance tradeoff; overfitting | Fit a regression model to calibrate a force sensor / estimate joint friction | Sensor calibration, system identification (static models) |
| 4 | Classification I: Logistic Regression, k-NN, SVM | Decision boundaries; margin-based classifiers; multiclass strategies | Classify machine operating states (normal/fault) from sensor features | Binary/multiclass fault detection in industrial equipment |
| 5 | Tree-Based Methods & Ensembles | Decision trees, random forests, gradient boosting; feature importance | Predict remaining useful life class (low/med/high risk) from vibration/temperature features | Predictive maintenance, feature importance for root-cause analysis |
| 6 | Unsupervised Learning: PCA & Clustering | Dimensionality reduction, k-means, DBSCAN; visualizing high-dimensional sensor data | Cluster machine states from unlabeled vibration spectra; anomaly flagging | Unsupervised anomaly detection when fault labels are unavailable |
| 7 | Model Evaluation, Validation & Tuning | Cross-validation, confusion matrices, ROC/precision-recall, grid/random search, pipelines | **Project Checkpoint 1**: deliver a validated classical ML pipeline on a real dataset | Rigorous evaluation for safety-relevant automation decisions |

### Part 2 — Deep Learning (PyTorch)

| Week | Topic | Learning Outcomes | Lab | Robotics / Automation Application |
|---|---|---|---|---|
| 8 | From scikit-learn to PyTorch: Neural Network Foundations | Perceptron → MLP; backpropagation; autograd; tensors; training loop mechanics | Build and train an MLP from scratch in PyTorch on tabular sensor data | Comparing classical vs. neural models on the same fault-detection task |
| 9 | Deep Learning in Practice | Optimizers (SGD, Adam), loss functions, regularization (dropout, batch norm), learning rate scheduling | Train an MLP to approximate inverse kinematics / robot dynamics residuals | Learning-based approximation of nonlinear robot models |
| 10 | Convolutional Neural Networks | Convolution/pooling; CNN architectures; transfer learning | Train a CNN for visual defect detection on an industrial images dataset | Automated visual quality inspection on a production line |
| 11 | Sequence Models: RNN, LSTM, and a first look at Transformers | Sequential data; vanishing gradients; LSTM/GRU; attention (conceptual) | Forecast a time-series signal (e.g., tool wear, temperature trend) with an LSTM | Predictive maintenance and trajectory/time-series forecasting |
| 12 | Reinforcement Learning Foundations | MDPs, value functions, Q-learning, policy gradient basics | Train a simple RL agent (e.g., cart-pole or a 2-DOF arm) in a simulated environment | Learning-based control policies for robotic tasks |
| 13 | From Model to Deployment | Sim-to-real gap, model compression/quantization, latency constraints, inference on embedded/edge hardware, basic ROS integration pattern | Export and benchmark a trained model for real-time inference | Deploying ML models on real robot/PLC-class hardware |
| 14 | Capstone Presentations & Responsible ML in Automation | Explainability, failure modes, safety considerations, monitoring in production | **Final Project Presentations** | Reflecting on when/why to trust an ML model in a safety-relevant loop |

---

## Semester Project (runs Weeks 2–14)

Students select one problem from a provided list (or propose their own) tied to a real or simulated robotics/automation dataset:
- Fault detection on a rotating machine (bearing/vibration dataset)
- Visual inspection of manufactured parts
- Predictive maintenance from multivariate sensor time series
- Learning a residual dynamics model for a robotic arm
- A simple RL-based controller in simulation

**Checkpoint 1 (Week 7):** classical ML baseline, properly validated.
**Final delivery (Week 14):** deep learning model compared against the baseline, with a short deployment/feasibility discussion.

---

## Assessment (suggested weighting)

| Component | Weight |
|---|---|
| Lab assignments (weekly) | 30% |
| Project checkpoint (Week 7) | 15% |
| Final project + presentation (Week 14) | 35% |
| Written exam (covers Weeks 1–11 concepts) | 20% |

---

## Tools & Environment

- **Language:** Python 3.x
- **Core libraries:** NumPy, Pandas, Matplotlib
- **Classical ML:** scikit-learn
- **Deep learning:** PyTorch (+ torchvision for CNN week)
- **Optional:** Gymnasium or PyBullet for the RL week; ONNX or TorchScript for the deployment week
- **Suggested datasets:** CWRU Bearing Dataset (fault detection), NASA C-MAPSS (predictive maintenance/RUL), a small custom or public defect-inspection image set, IMU/force-torque logs (can be simulated if lab hardware is unavailable)

---

## Suggested References

- Géron, *Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow* (for the classical ML half's structure and intuition)
- Goodfellow, Bengio, Courville, *Deep Learning* (conceptual grounding for Part 2)
- Sutton & Barto, *Reinforcement Learning: An Introduction* (Week 12)
- Selected papers on learning-based control and sim-to-real transfer, assigned as short readings in Weeks 12–13

---

## Notes for the Instructor

- Weeks 1 and 8 are the two "reset" points — most student attrition/confusion in an ML course for non-CS majors happens at the notation and tooling level, not the math. Budget extra lab-support time there.
- If lab access to real hardware is limited, simulated datasets (Gazebo/PyBullet logs, synthetic sensor noise) work fine for Weeks 2–9 and 12; try to keep at least one real dataset (e.g., CWRU bearings) for the project so students see real noise and label imbalance.
- Week 13 (deployment) is often skipped in generic ML courses but is exactly what differentiates this course for a controls/robotics audience — consider protecting it from schedule slippage.
