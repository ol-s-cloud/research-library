# Data Sources - GNN Electricity Price Forecasting

Comprehensive data requirements and access procedures for developing Graph Neural Network-based electricity price forecasting models.

## 🎯 Data Requirements Overview

### Primary Data Sources (Critical)
- **EPEX SPOT**: European electricity market prices and volumes
- **ENTSO-E**: European transmission system data
- **National Grid ESO**: UK electricity system data
- **Weather APIs**: Meteorological data for renewable forecasting

### Secondary Data Sources (Enhancement)
- **Grid Topology Data**: Network structure and constraints
- **Fuel Price Data**: Gas, coal, carbon prices
- **Renewable Generation**: Solar and wind generation data
- **Demand Patterns**: Historical consumption patterns by sector

## 📊 Detailed Data Specifications

### 1. EPEX SPOT (European Power Exchange)

**Data Required:**
- Hourly day-ahead electricity prices (€/MWh)
- Intraday auction and continuous trading prices
- Trading volumes and liquidity metrics
- Cross-border capacity allocation results

**Geographic Coverage:**
- Germany, France, Netherlands, Belgium (Phase 1)
- Austria, Switzerland (Phase 2)
- All EPEX coupled markets (Phase 3)

**Temporal Coverage:**
- Historical: 5+ years (2019-2024)
- Real-time: Live data feed for model validation
- Granularity: Hourly, 15-minute intervals where available

**Access Procedure:**
1. **Registration**: Create EPEX SPOT data portal account
2. **Application**: Submit research data request form
3. **Approval**: Academic license review (4-6 weeks)
4. **Agreement**: Sign data usage agreement
5. **Access**: API credentials and documentation

**Cost Structure:**
- Academic License: €5,000-€15,000/year
- Free Tier: Limited historical data (6 months)
- Real-time Feed: Additional €10,000/year

**Contact Information:**
- **Email**: data-services@epexspot.com
- **Website**: https://www.epexspot.com/en/market-data
- **Phone**: +33 1 73 03 61 10

**Status**: 🟡 Application submitted, awaiting approval

### 2. ENTSO-E (European Network of Transmission System Operators)

**Data Required:**
- Transmission capacity and flow data
- Generation forecasts by fuel type
- Actual vs. forecasted demand
- Cross-border transmission schedules
- Grid topology and network structure

**API Endpoints:**
- Generation forecasts and actual generation
- Load forecasts and actual demand
- Cross-border physical flows
- Balancing market data
- Transmission network maintenance schedules

**Access Procedure:**
1. **Registration**: ENTSO-E Transparency Platform account
2. **API Access**: Request API token (immediate)
3. **Rate Limits**: 400 requests per minute
4. **Documentation**: https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html

**Cost Structure:**
- **Free Tier**: Basic historical and real-time data
- **Commercial**: Enhanced data and higher rate limits
- **Academic**: Full access with proper documentation

**Contact Information:**
- **Email**: transparency@entsoe.eu
- **API Documentation**: https://transparency.entsoe.eu/

**Status**: ✅ Free access secured, commercial license pending

### 3. National Grid ESO (UK System Operator)

**Data Required:**
- Balancing mechanism prices and volumes
- System frequency and voltage data
- Demand forecasts and actual demand
- Generation mix and renewable output
- Interconnector flows (GB-FR, GB-NL, GB-BE)

**API Endpoints:**
- Carbon Intensity API
- Balancing Mechanism Reporting System (BMRS)
- Data Portal API
- Embedded Wind and Solar Forecasts (EWSF)

**Access Procedure:**
1. **Registration**: National Grid Data Portal account
2. **API Access**: Immediate for most public data
3. **Enhanced Access**: Application for detailed grid data
4. **Documentation**: https://www.nationalgrideso.com/data-portal

**Cost Structure:**
- **Public APIs**: Free access
- **Detailed Grid Data**: Subscription required
- **Real-time Feeds**: Commercial licensing

**Contact Information:**
- **Email**: box.ESO.DataPortal@nationalgrideso.com
- **API Portal**: https://data.nationalgrideso.com/

**Status**: ✅ Public API access secured

### 4. Weather Data Sources

#### OpenWeatherMap
**Data Required:**
- Temperature, humidity, wind speed/direction
- Solar irradiance and cloud cover
- Precipitation and visibility
- Historical and forecast data

**Access Procedure:**
1. Account registration
2. API key generation (immediate)
3. Select appropriate pricing plan

**Cost**: $40-$180/month for required data volume
**Status**: ✅ API access secured

#### MetOffice (UK)
**Data Required:**
- High-resolution weather forecasts
- Renewable energy weather data
- Climate data for long-term analysis

**Access**: DataPoint API, research agreements available
**Status**: 🟡 Exploring academic access

### 5. Grid Topology and Network Data

**Sources Required:**
- **ENTSO-E**: European network topology
- **National Grid**: UK transmission network
- **Academic Datasets**: IEEE test systems, synthetic networks

**Challenges:**
- Commercial sensitivity of detailed grid data
- Security restrictions on critical infrastructure data
- Data standardization across different TSOs

**Alternative Approaches:**
- Use aggregated/anonymized network representations
- Synthetic network generation based on public information
- Partnership with TSOs for research purposes

**Status**: 🟡 Investigating access options

### 6. Fuel Price Data

**Sources:**
- **ICE**: Natural gas futures prices
- **EEX/EUA**: Carbon emission allowances
- **Platts/Argus**: Coal and oil prices
- **NBP/TTF**: Gas hub prices

**Access**: Most available through financial data providers
**Cost**: $1,000-$5,000/month for comprehensive coverage
**Status**: 🟡 Evaluating options

## 🔄 Data Processing Pipeline

### 1. Data Ingestion
```python
# Example data fetching workflow
from epex_api import EPEXClient
from entsoe_api import ENTSOEClient
from weather_api import WeatherClient

# Initialize API clients
epex = EPEXClient(api_key="your_key")
entsoe = ENTSOEClient(api_key="your_key")
weather = WeatherClient(api_key="your_key")

# Fetch coordinated data
prices = epex.get_day_ahead_prices(start_date, end_date)
demand = entsoe.get_load_data(start_date, end_date)
weather_data = weather.get_historical_data(locations, start_date, end_date)
```

### 2. Data Validation
- **Completeness**: Check for missing timestamps
- **Consistency**: Validate cross-source data alignment
- **Quality**: Detect outliers and anomalies
- **Timeliness**: Ensure data freshness for real-time models

### 3. Data Transformation
- **Harmonization**: Standardize time zones and units
- **Feature Engineering**: Create derived variables
- **Graph Construction**: Build network representations
- **Preprocessing**: Normalization and scaling

## 📋 Data Access Action Items

### Immediate Actions (Week 1-2)
- [ ] Submit EPEX SPOT academic data request
- [ ] Register for enhanced ENTSO-E access
- [ ] Set up OpenWeatherMap API integration
- [ ] Configure data storage infrastructure

### Short-term Actions (Month 1)
- [ ] Implement data ingestion pipeline
- [ ] Develop data validation procedures
- [ ] Create data processing documentation
- [ ] Establish data backup and versioning

### Medium-term Actions (Month 2-3)
- [ ] Negotiate grid topology data access
- [ ] Integrate fuel price data sources
- [ ] Develop real-time data streaming
- [ ] Implement data quality monitoring

## 💰 Budget Requirements

| Data Source | Annual Cost | Priority | Status |
|-------------|-------------|----------|--------|
| EPEX SPOT Academic License | €10,000 | Critical | Pending |
| ENTSO-E Commercial Access | €5,000 | High | Pending |
| Weather APIs (Multiple) | $2,000 | High | Secured |
| Fuel Price Data | $15,000 | Medium | Evaluating |
| Grid Topology Data | Negotiable | Medium | Investigating |
| **Total Estimated** | **€25,000** | - | - |

## 🤝 Partnership Opportunities

### Data Sharing Partnerships
- **Universities**: Joint data procurement and sharing
- **Industry**: Data access in exchange for research insights
- **Government**: Access to regulatory and statistical data
- **TSOs**: Direct partnerships for grid data access

### Collaboration Benefits
- Cost sharing for expensive data licenses
- Access to proprietary datasets
- Real-world validation opportunities
- Industry feedback and requirements

## 📞 Contact for Data Access

**Data Procurement Lead**: [Your Name]  
**Email**: [data-access@institution.edu]  
**Phone**: [Your Phone Number]  
**Institution**: [Your Institution]  

**Administrative Support**:  
**Email**: [admin@institution.edu]  
**Legal/Contracts**: [legal@institution.edu]  

---

*Last Updated: May 2025*  
*Next Review: June 2025*  
*Document Version: 1.0*