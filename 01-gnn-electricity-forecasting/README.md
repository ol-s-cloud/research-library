# GNN Electricity Price Forecasting

Advanced electricity price forecasting using Graph Neural Networks (GNNs) to capture spatial-temporal dependencies in European electricity markets, with extension to UK and US markets.

## Project Status

[![Project Status](https://img.shields.io/badge/status-research-blue)](PROJECT_STATUS.md)
[![Sprint](https://img.shields.io/badge/sprint-1-orange)](SPRINT_STATUS.md)
[![Data Access](https://img.shields.io/badge/data-pending-yellow)](DATA_SOURCES.md)
[![Model Development](https://img.shields.io/badge/model-design-green)](GAP_ANALYSIS.md)

**Project Documentation:**
- [📊 Project Status](PROJECT_STATUS.md) - Development progress and milestones
- [🔍 Gap Analysis](GAP_ANALYSIS.md) - Current vs. target state analysis
- [🏃 Sprint Status](SPRINT_STATUS.md) - Current sprint goals and achievements
- [🔒 Audit Framework](AUDIT_FRAMEWORK.md) - Testing and validation guidelines
- [🤝 Contribution Guidelines](CONTRIBUTION.md) - How to contribute to this research
- [📈 Evaluation Framework](EVALUATION.md) - Success metrics and validation methods
- [🗂️ Data Sources](DATA_SOURCES.md) - Required data sources and access procedures

## Overview

This research project develops state-of-the-art electricity price forecasting models using Graph Neural Networks to capture complex interdependencies between different market zones, generation sources, and transmission constraints. The model aims to improve upon traditional time-series forecasting by explicitly modeling the graph structure of electricity markets.

## Research Objectives

- **Primary**: Develop GNN-based forecasting models that outperform traditional time-series methods
- **Secondary**: Create interpretable models that can explain price formation mechanisms
- **Tertiary**: Enable real-time forecasting for intraday and day-ahead markets
- **Impact**: Provide 15-20% improvement in forecasting accuracy over baseline models

## Technical Approach

### Model Architecture
- **Graph Construction**: Market zones as nodes, transmission lines as edges
- **Node Features**: Historical prices, demand, generation mix, weather
- **Edge Features**: Transmission capacity, flow constraints, congestion
- **Temporal Modeling**: LSTM/GRU layers for time-series dependencies
- **Spatial Modeling**: GraphSAGE/GAT for spatial dependencies

### Implementation Framework
- **Deep Learning**: PyTorch Geometric for GNN implementation
- **Data Processing**: Pandas, NumPy for data manipulation
- **Visualization**: Plotly, Matplotlib for result visualization
- **Deployment**: MLflow for model tracking and deployment

## Geographic Scope

### Phase 1: European Markets
- **Primary Markets**: Germany, France, Netherlands, Belgium
- **Data Source**: EPEX SPOT, ENTSO-E
- **Timeline**: 6 months

### Phase 2: UK Market Extension
- **Market**: Great Britain electricity market
- **Data Source**: Elexon, National Grid ESO
- **Integration**: Cross-channel interconnector modeling
- **Timeline**: 3 months

### Phase 3: US Market Adaptation
- **Markets**: PJM, CAISO, ERCOT
- **Challenges**: Different market structures and regulations
- **Timeline**: 6 months

## Data Requirements

### Critical Data Sources
1. **EPEX SPOT**: Hourly electricity prices, trading volumes
2. **ENTSO-E**: Transmission data, generation forecasts, actual demand
3. **Weather APIs**: Temperature, wind speed, solar irradiance
4. **Grid Topology**: Transmission network structure and capacities

### Data Access Status
- ⏳ **EPEX SPOT**: Application submitted, awaiting approval
- ⏳ **ENTSO-E**: Free tier available, commercial license pending
- ✅ **OpenWeatherMap**: API access secured
- ⏳ **Grid Topology**: Requesting from national TSOs

See [DATA_SOURCES.md](DATA_SOURCES.md) for detailed data requirements and access procedures.

## Expected Outcomes

### Academic Impact
- 2-3 high-impact journal publications
- Conference presentations at top energy/AI venues
- Open-source model implementation

### Industry Applications
- Energy trading strategy optimization
- Grid planning and investment decisions
- Renewable energy integration planning
- Risk management for energy portfolios

### Methodological Contributions
- Novel GNN architectures for energy forecasting
- Transfer learning approaches for cross-market adaptation
- Interpretability methods for complex energy models

## Success Metrics

- **Forecasting Accuracy**: 15-20% MAPE improvement over baseline
- **Model Interpretability**: 80% stakeholder comprehension rate
- **Computational Efficiency**: <10 minutes for daily forecast updates
- **Generalization**: Successful deployment in 3+ different markets

See [EVALUATION.md](EVALUATION.md) for detailed evaluation framework.

## Getting Started

### Prerequisites
```bash
# Python environment setup
python -m venv gnn-forecasting
source gnn-forecasting/bin/activate  # On Windows: gnn-forecasting\Scripts\activate

# Install dependencies
pip install torch torch-geometric pandas numpy matplotlib plotly scikit-learn
pip install mlflow wandb  # For experiment tracking
```

### Initial Setup
```bash
# Clone and navigate to project
cd 01-gnn-electricity-forecasting

# Install project dependencies
pip install -r requirements.txt

# Set up data directories
mkdir -p data/{raw,processed,external}
mkdir -p models experiments results
```

### Data Preparation
1. Request data access following [DATA_SOURCES.md](DATA_SOURCES.md)
2. Run data preprocessing pipeline
3. Validate data quality and completeness
4. Generate graph structure from network topology

## Project Structure

```
01-gnn-electricity-forecasting/
├── src/
│   ├── data/              # Data processing and loading
│   ├── models/            # GNN model implementations
│   ├── training/          # Training loops and optimization
│   ├── evaluation/        # Model evaluation and metrics
│   └── utils/             # Utility functions
├── notebooks/             # Jupyter notebooks for exploration
├── tests/                 # Unit and integration tests
├── configs/               # Configuration files
├── data/                  # Data storage (not in git)
├── models/                # Trained model storage
├── results/               # Experiment results and plots
└── docs/                  # Additional documentation
```

## Current Development Sprint

See [SPRINT_STATUS.md](SPRINT_STATUS.md) for current sprint objectives and progress.

**Sprint 1 Focus**: Data acquisition and preprocessing pipeline development

## Collaboration Opportunities

- **Data Partnerships**: Seeking partnerships with electricity market operators
- **Academic Collaboration**: Joint research with energy economics and ML groups
- **Industry Pilots**: Testing with energy trading companies and utilities
- **Student Projects**: MSc/PhD thesis opportunities available

See [CONTRIBUTION.md](CONTRIBUTION.md) for detailed collaboration guidelines.


## License

This research project is released under the MIT License for open science collaboration.

---

*Last Updated: May 2025*  
*Project Version: 1.0*  
*Status: Active Research*
