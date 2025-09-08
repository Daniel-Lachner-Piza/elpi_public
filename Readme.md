# ELPI (EEG Labeling and Processing Interface) User's Guide

## Table of Contents

1. [Overview](#overview)
2. [System Requirements](#system-requirements)
3. [Getting Started](#getting-started)
4. [Initial Setup](#initial-setup)
5. [Core Features](#core-features)
6. [Typical Workflow](#typical-workflow)
7. [Visual Interface Components](#visual-interface-components)
8. [Annotation System](#annotation-system)
9. [Signal Processing and Filtering](#signal-processing-and-filtering)
10. [Detection and Analysis Tools](#detection-and-analysis-tools)
11. [Data Export and Import](#data-export-and-import)
12. [Quality Assessment](#quality-assessment)
13. [Advanced Features](#advanced-features)
14. [Troubleshooting](#troubleshooting)
15. [Keyboard Shortcuts](#keyboard-shortcuts)

## Overview

ELPI (EEG Labeling and Processing Interface) is a MATLAB-based application designed for informed EEG signal analysis and annotation. The system supports both scalp and intracranial EEG recordings and provides advanced tools for signal visualization, filtering, event detection, and annotation management.

### Key Capabilities:
- Multi-format EEG file support (EDF, LAY, BrainVision, Micromed files) (Fieldtrip supported!)
- Interactive EEG visualization with multiple time scales
- Advanced filtering and signal processing
- Interactive event annotation
- Noise analysis
- Occurrence rate reporting
- Data export capabilities

## System Requirements

- MATLAB R2023b:
    - Computer Vision Toolbox
    - Image Processing Toolbox
    - Signal Processing Toolbox
    - Statistics and Machine Learning Toolbox
    - Wavelet Toolbox
- FieldTrip toolbox (automatically initialized)
- Sufficient RAM for EEG file processing (recommended: 16GB+)
- Compatible EEG file formats: EDF, EDF+, LAYDAT, VHDR, TRC

## Getting Started

### 1. Launch ELPI

1. Download elpi_public folder
2. Run the elpi.exe
3. Chech Display settings, Zoom should be set to 100%, (not more!), otherwise the wiindows will not scale correctly

### 2. Load EEG Data

1. Click **"Open EEG File"** in the main settings window
2. Select your EEG file (e.g.: .edf, .lay, .vhdr)
3. The system will automatically detect sampling rate and channel configuration

## Initial Setup

### EEG Type Selection

Choose the appropriate EEG type:
- **Scalp EEG**: For surface electrodes
- **Intracranial**: For depth electrodes, grids, and strips

### Channel Configuration

1. **Scalp EEG Options**:
   - Physical Reference
   - Bipolar Montages (Longitudinal Bipolar)

2. **Intracranial Options**:
   - Bipolar montages automatically generated from electrode pairs

### Filter Setup

Configure up to 4 bandpass filters:
- **Filter 1**: Broad band (default: 1-40 Hz) - for general EEG viewing
- **Filter 2**: HFO band (default: 80-500 Hz) - for high-frequency oscillations
- **Filter 3**: Ripple band (default: 80-250 Hz) - for ripple detection
- **Filter 4**: Fast Ripple band (default: 250-500 Hz) - for fast ripple detection

These filters have default values for HFO annotation. The filters can be adjusted to annotate other events like sleep-spindles.

### Wavelet Analysis

Set parameters for time-frequency analysis:
- **Min Frequency**: Lower bound for spectrogram (default: 60 Hz)
- **Max Frequency**: Upper bound for spectrogram (default: 500 Hz)
- **Steps**: Frequency resolution

## Core Features

### 1. Multi-Panel Display System

**Three Main Visualization Panels:**

#### Big Window (Top Panel)
- Overview display showing multiple channels
- Configurable time window (default: 10 seconds)
- Navigation and channel selection
- Annotation overlay display

#### Small Window (Middle Panel)
- Zoomed view of selected channel
- Higher temporal resolution (default: 1 second)
- Detailed signal examination
- Precise annotation placement

#### Heatmap/Spectrogram (Bottom Panel)
- Time-frequency representation
- Wavelet-based analysis
- Frequency range: configurable (60-500 Hz default)
- Color-coded power representation

### 2. Navigation System

**Horizontal Navigation:**
- Left/Right arrow keys: Navigate through time

**Vertical Navigation:**
- Up/Down arrow keys: adjust sensitivity

**Window Controls:**
- Sliders for adjusting window position
- Window length adjustment controls

## Typical Workflow

### Step 1: Load and Configure EEG

1. **Launch ELPI**

2. **Load EEG File**
   - Click "Open EEG File"
   - Navigate to your EEG file (e.g.: .edf )
   - Wait for file loading and processing

3. **Configure Settings**
   - Select EEG type (Scalp/Intracranial)
   - Choose appropriate montage
   - Select channels to display
   - Configure filter settings
   - Set wavelet analysis parameters

4. **Start EEG Reviewer**
   - Click "Start EEG Reviewer" button
   - Main annotation interface will open

### Step 2: Navigate and Examine Signals

1. **Initial View**
   - Big window shows overview of multiple channels
   - Small window shows detailed view of selected channel
      - To select channel simply click on the label or on the signal
   - Heatmap shows time-frequency content

2. **Navigation**
   - Use arrow keys to move through time
   - Click on channels in big window to select for detailed view
   - Use sliders for quick navigation
   - Check noise index indicators for data quality

3. **Adjust Display**
   - Use filter buttons to rotate through the filters
   - Adjust window lengths as needed
   - Toggle channel visibility with button

### Step 3: Annotate Events

1. **Select Annotation Type**
   - Go to Annotations → Select type to mark
   - Choose from: HFO, Ripple, FR, IED, Spindle, Noise, Bad
   - Add annotation types if needed

2. **Mark Events**
   - Click and drag on the signal to create annotations
   - Use right-click for additional options
   - Events automatically saved with timestamps

3. **Edit Annotations**
   - Activate annotation mode by clicking on button
   - For single channel annotations:
      - Press s key
      - Draw rectangle around the signal where you want to place your annotation
   - For multi-channel annotations:
      - Press a key
      - Draw rectangle around the signal where you want to place your annotation 
   - Double-click existing annotations to edit
   - Modify start/end times, type, or comments
   - Add multi-channel annotations as needed

4. **Review Annotations**
   - Go to Annotations → Show List to view all events
   - Navigate between events using Up/Down keys

### Step 4: Quality Assessment

1. **Monitor Noise Index**
   - Check real-time noise indicators
   - View noise map for overall recording quality
   - Identify problematic segments

2. **Mark Bad Segments**
   - Go to Segments → Edit Bad Segments
   - Mark periods of poor signal quality
   - Exclude from analysis and reports

### Step 5: Analysis and Export

1. **Generate Reports**
   - Go to Reports → Occurrence Rate
   - Export results to files

2. **Export Data**
   - Save annotations to file formats
   - Export EDF clips of interesting segments
   - Save processed signals

## Visual Interface Components

### Menu System

**File Menu:**
- Open: Load EEG files
- Export: Save current EEG segment as EDF

**Channels Menu:**
- Channel selector with filtering options
- Multi-channel selection capabilities

**Annotations Menu:**
- Settings: Configure annotation types and colors
- Traverse Style: when navigating through events list, show all channels or just the one channel with the event
- Select type to mark: Choose annotation category
- Select type to show: Filter displayed annotations
- Load/Save: Import/export annotation files
- Show List: View all annotations in tabular format
- Clear All: Remove all annotations

**Segments Menu:**
- Edit Bad Segments: Mark poor quality periods

**Reports Menu:**
- Occurrence Rate: Generate statistical reports

**Filters Menu:**
- Notch: Configure power line noise filtering
- NoiseMap: Display signal quality assessment

### Control Elements

**Filter Buttons:**
- Cycle through configured bandpass filters
- Real-time filter switching
- Visual indication of active filter

**Sliders and Input Fields:**
- Big Window: Position and length controls
- Small Window: Position and length controls
- Numeric input for precise values

## Annotation System

### Annotation Types

**Default Event Types:**
- **IED**: Interictal Epileptiform Discharges
- **HFO**: High-Frequency Oscillations (general)
- **Ripple**: Ripples (80-250 Hz)
- **FR**: Fast Ripples (250-500 Hz)
- **Spindle**: Sleep Spindles
- **Noise**: Noise artifacts
- **Bad**: Bad signal segments

### Annotation Properties

Each annotation contains:
- **Channel**: Source channel or multi-channel flag
- **Type**: Event classification
- **Start Time**: Event onset (seconds)
- **End Time**: Event offset (seconds)
- **Start Sample**: Sample number of onset
- **End Sample**: Sample number of offset
- **Comments**: User-defined notes
- **Channel Specific**: Single vs. multi-channel flag
- **Creation Time**: Timestamp of annotation
- **Username**: Annotator identification

### Annotation Workflow

1. **Enable Marking Mode**
   - Marking mode lamp indicates active state

2. **Create Annotations**
   - Click and drag on signal in either panel
   - Release to complete annotation
   - Automatic time calculation and sample conversion

3. **Edit Existing Annotations**
   - Double-click on annotation
   - Event Editor opens with all properties
   - Modify times, type, comments, etc.

4. **Navigation Between Events**
   - Use annotation traversing functions
   - Jump to next/previous events of selected type

### Annotation File Formats

**Supported Import/Export:**
- MATLAB .mat files
- ELPI native format with full metadata
- LAY file integration for Persyst compatibility

## Signal Processing and Filtering

### Bandpass Filtering

**Four Configurable Filters:**
- Independent low and high cutoff frequencies
- Real-time filter switching during review

**Filter Applications:**
- Filter 1: General EEG (1-40 Hz)
- Filter 2: HFO detection (80-500 Hz)
- Filter 3: Ripple analysis (80-250 Hz)
- Filter 4: Fast Ripple analysis (250-500 Hz)

### Notch Filtering

**Line Noise Removal:**
- Configurable for 50 Hz or 60 Hz systems
- Multiple harmonic removal (up to 20 harmonics)
- Channel-specific application
- Adjustable filter order

**Features:**
- European/American power system presets
- Real-time application
- Minimal signal distortion

### Wavelet Analysis

**Time-Frequency Decomposition:**
- Continuous Wavelet Transform (CWT)
- Morlet wavelet basis
- Configurable frequency range
- Real-time spectrogram display

**Applications:**
- HFO visualization
- Frequency content analysis
- Time-frequency event characterization

## Detection and Analysis Tools

### Noise Analysis

**Real-Time Quality Assessment:**
- Continuous noise index calculation
- Channel-specific quality metrics
- Overall recording quality assessment
- Visual quality mapping

**Quality Indicators:**
- Green: Good signal quality (NI < 0.1)
- Red: Poor signal quality (NI > 0.1)
- Real-time updating during review

## Data Export and Import

### EEG File Export

**EDF Export:**
- Extract specific time segments
- Maintain original signal characteristics
- Configurable start/end times
- Clinical-grade format compliance

### Annotation Export

**Format Options:**
- MATLAB .mat files with full metadata
- LAY file integration
- CSV export for statistical analysis
- Custom format definitions

### Batch Processing

**Capabilities:**
- Multiple file processing
- Automated annotation detection
- Batch quality assessment
- Report generation

## Quality Assessment

### Noise Index System

**Real-Time Monitoring:**
- Spectral analysis-based quality metrics
- Channel-specific noise assessment
- Temporal quality tracking
- Visual feedback system

**Quality Metrics:**
- Overall recording noise index
- Current window noise index
- Channel-specific quality indicators
- Bad segment identification

### Noise Map

**Visualization:**
- Time-based quality representation
- Color-coded quality levels
- Interactive navigation
- Pattern recognition for artifacts

## Other Features

### Automation Features

**Auto-save Functionality:**
- Configurable batch sizes (default: 50 annotations)
- Automatic backup creation
- Recovery mechanisms
- Progress tracking


## Troubleshooting

### Common Issues

**Buttons not visible, Window not scaling correctly:**
- Set display zoom level to 100%

**Performance Issues:**
- Plug in computer to power supply!
- Close unnecessary applications
- Reduce number of displayed channels
- Lower filter orders if needed
- Elpi runs extremely slow on Matlab 2025, stick to Matlab2023a or Matlab2023b and performance should be fine

### Error Messages

**"Sampling Rate too low":**
- Ensure sampling rate > 1000 Hz for HFO analysis
- Check file header information
- Consider resampling if necessary

**"No EEG channels found":**
- Verify channel labels in file
- Check montage configuration
- Ensure proper file format

---

*Version: 2025.1*
*Last Updated: September 2025*
