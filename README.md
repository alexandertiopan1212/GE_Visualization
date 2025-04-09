
# 📊 GE McKinsey Matrix Visualization

> A strategic analysis tool to visualize product portfolio positioning using the **GE McKinsey Matrix**. This project helps assess products based on their market attractiveness and business strength using data-driven scoring and visualization.

---

## 📌 Project Overview

The goal of this project is to utilize the **GE McKinsey Matrix methodology** to assess and visualize the strategic positioning of various products within a market. The matrix helps businesses evaluate their product lines based on two key dimensions:

- **Market Attractiveness**
- **Business Strength**

The matrix is plotted as a bubble chart to clearly identify product positioning and strategic recommendations.

---

## 🛠️ Libraries Used

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

---

## 📂 Input & Assumptions

- Data is read from `table.xlsx`
- Missing values are replaced with 0
- Weights are applied to multiple metrics to compute:
  - **Market Attractiveness**: market size, market share, industry growth
  - **Business Strategy**: revenue (recurring/nonrecurring), margin, cost structure

---

## 🧮 Scoring Weights

```python
# Market Attractiveness Weights
market_share_weight = 0.20
market_size_weight = 0.40
industry_growth_weight = 0.40

# Business Strategy Weights
revenue_recurring_weight = 0.2
revenue_nonrecurring_weight = 0.10
biaya_fix_weight = 0.2
biaya_variabel_weight = 0.1
margin_weight = 0.4
```

Each metric is ranked and multiplied by its corresponding weight to get final scores.

---

## 📈 Visualization Logic

A bubble chart is plotted using the following logic:

- **X-axis**: Business Strength Score
- **Y-axis**: Market Attractiveness Score
- **Bubble Size**: Scaled by market size
- **Color**: Randomized for visual distinction

```python
quadrant_chart(
    name = np.array(data['produk']),
    x=np.array(data['revenue_recurring'] + data['revenue_nonrecurring'] + data['biaya_variabel'] + data['biaya_fix'] + data['margin']),
    y=np.array(data['market_share'] + data['market_size']) + data['industry_growth'],
    colors = np.array(data['colors']),
    bubble_size = np.array(data['bubble_size']),
    xtick_labels=['Low', 'High'],
    ytick_labels=['Low', 'High']
)
```

The quadrant lines are plotted based on the average scores to help identify product positioning:

- Top-right: Invest/Grow
- Bottom-left: Divest
- Others: Selective strategies

---

## 📊 Output

The final output is a **GE Matrix** that visually maps each product’s strategic position, aiding decision-makers in determining which products to prioritize, invest in, or phase out.

---

## 📁 Repository Structure

```
GE_Visualization/
├── main.ipynb       # Full analysis and plotting logic
├── table.xlsx       # Input data for scoring
└── readme.md        # You're here
```

---

## 👤 Author

**Alexander Tiopan**  
📧 alexandertiopan1212@gmail.com  
🔗 GitHub: [alexandertiopan1212](https://github.com/alexandertiopan1212)

---

## 📝 Source

Based on: [Strategic Management Insight – GE McKinsey Matrix](https://strategicmanagementinsight.com/tools/ge-mckinsey-matrix)
