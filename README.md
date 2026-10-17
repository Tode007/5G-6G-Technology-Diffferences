# 5G-6G-Technology-Diffferences
Conducted a comparative analysis of 5G and emerging 6G technologies, focusing on data rates, frequency bands, latency, signal-to-noise ratio (SNR), and spectral efficiency. 


import matplotlib.pyplot as plt
import numpy as np

# 1. Define the performance metrics and their raw values
labels = [
    'Peak Data Rate\n(5G: 20 Gbps | 6G: 1000 Gbps)',
    'User Experience Rate\n(5G: 100 Mbps | 6G: 1000 Mbps)',
    'Latency Improvement\n(5G: 1ms | 6G: 0.1ms)',
    'Spectral Efficiency\n(6G is ~3x higher)',
    'Mobility Support\n(5G: 500 km/h | 6G: 1000 km/h)'
]

# Normalized values (5G is set as the baseline baseline = 1.0)
# 6G metrics are scaled as a factor of improvement over 5G
d=normalized = [1.0, 1.0, 1.0, 1.0, 1.0]
c=normalized = [50.0, 10.0, 10.0, 3.0, 2.0]  # e.g., 50x peak rate, 10x latency improvement

# 2. Set up the radar chart geometry
num_vars = len(labels)
angles = np.linspace(0, 2 * np.pi, num_vars, endpoint=False).tolist()

# The radar chart requires the loop to close, so append the start value to the end
d += d[:1]
c+= c[:1]
angles += angles[:1]

# 3. Plotting configuration
fig, ax = plt.subplots(figsize=(8, 8), subplot_kw=dict(polar=True))

# Draw the 5G baseline outline and fill
ax.plot(angles, d, color='#0066cc', linewidth=2, label='5G Network (Baseline)')
ax.fill(angles, d, color='#0066cc', alpha=0.25)

# Draw the 6G target outline and fill
ax.plot(angles, c, color='#ff6600', linewidth=2, label='6G Network (Projected Target)')
ax.fill(angles, c, color='#ff6600', alpha=0.15)

# Fix axis labels to match the metrics
ax.set_theta_offset(np.pi / 2)
ax.set_theta_direction(-1)
plt.xticks(angles[:-1], labels, color='black', size=10)

# Set logarithmic scale behavior for the radial axis to handle the 50x leap clearly
ax.set_rscale('symlog', linthresh=1.0)
ax.set_rlabel_position(30)
plt.yticks([1, 2, 5, 10, 20, 50], ["1x", "2x", "5x", "10x", "20x", "50x"], color="grey", size=9)
plt.ylim(0, 60)

# 4. Titles and Legends
plt.title('Key Performance Parameter (KPP) Multipliers\n6G Target Specs vs. 5G Baseline', size=14, weight='bold', pad=20)
plt.legend(loc='upper right', bbox_to_anchor=(1.2, 1.1))

# Optimize layout and display
plt.tight_layout()
plt.show()
s
