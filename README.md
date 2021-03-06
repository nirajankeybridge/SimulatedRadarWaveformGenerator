# Simulated Radar Waveform and RF Dataset Generator for Incumbent Signals in the 3.5 GHz CBRS Band
<!-- TOC -->

- [1. Legal Disclaimers](#1-legal-disclaimers)
    - [1.1. Software Disclaimer](#11-software-disclaimer)
    - [1.2. Commercial Disclaimer](#12-commercial-disclaimer)
- [2. Project Summary](#2-project-summary)
    - [2.1. Design Methodology](#21-design-methodology)
        - [2.1.1. Framework](#211-framework)
        - [2.1.2. GUI](#212-gui)
- [3. Development Details](#3-development-details)
- [4. How to run](#4-how-to-run)
    - [4.1. Run in MATLAB](#41-run-in-matlab)
    - [4.2. Run from Deployed executable](#42-run-from-deployed-executable)
        - [4.2.1. Compile from source](#421-compile-from-source)
        - [4.2.2. Precompiled Executable](#422-precompiled-executable)
- [5. Prerequisites:](#5-prerequisites)

<!-- /TOC -->

# 1. Legal Disclaimers
## 1.1. Software Disclaimer
 NIST-developed software is provided by NIST as a public service. 
 You may use, copy and distribute copies of the software in any medium,
 provided that you keep intact this entire notice. You may improve,
 modify and create derivative works of the software or any portion of
 the software, and you may copy and distribute such modifications or
 works. Modified works should carry a notice stating that you changed
 the software and should note the date and nature of any such change.
 Please explicitly acknowledge the National Institute of Standards and
 Technology as the source of the software.
 
 NIST-developed software is expressly provided "AS IS." NIST MAKES NO
 WARRANTY OF ANY KIND, EXPRESS, IMPLIED, IN FACT OR ARISING BY
 OPERATION OF LAW, INCLUDING, WITHOUT LIMITATION, THE IMPLIED WARRANTY
 OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, NON-INFRINGEMENT
 AND DATA ACCURACY. NIST NEITHER REPRESENTS NOR WARRANTS THAT THE
 OPERATION OF THE SOFTWARE WILL BE UNINTERRUPTED OR ERROR-FREE, OR
 THAT ANY DEFECTS WILL BE CORRECTED. NIST DOES NOT WARRANT OR MAKE ANY 
 REPRESENTATIONS REGARDING THE USE OF THE SOFTWARE OR THE RESULTS 
 THEREOF, INCLUDING BUT NOT LIMITED TO THE CORRECTNESS, ACCURACY,
 RELIABILITY, OR USEFULNESS OF THE SOFTWARE.
 
 You are solely responsible for determining the appropriateness of
 using and distributing the software and you assume all risks
 associated with its use, including but not limited to the risks and
 costs of program errors, compliance with applicable laws, damage to 
 or loss of data, programs or equipment, and the unavailability or
 interruption of operation. This software is not intended to be used in
 any situation where a failure could cause risk of injury or damage to
 property. The software developed by NIST employees is not subject to
 copyright protection within the United States.

 See [NIST Software Disclaimer](https://www.nist.gov/disclaimer) for more details.

## 1.2. Commercial Disclaimer
 Certain commercial equipment, instruments, or materials are identified in this README to foster understanding. Such identification does not imply recommendation or endorsement by the National Institute of Standards and Technology, nor does it imply that the materials or equipment identified are necessarily the best available for the purpose.
 
# 2. Project Summary

The simulated radar waveform generator is a software tool built with MATLAB to generate radar waveform datasets. The datasets can be used to develop and test detection algorithms for the 3.5 GHz CBRS or similar bands where the primary users of the band are federal incumbent radar systems. The software tool generates radar waveforms and randomizes the radar waveform parameters. The ranges of parameters values are selected based on NTIA testing procedures for ESC certification [1]. The parameters are pulse modulation, pulse duration, pulse repetition rate, chirp width and pulses per burst. In addition, we randomize the following parameters: start time, SNR, and the baseband center frequency of the radar signal.  

## 2.1. Design Methodology
This software consists of a MATLAB code and a graphical user interface (GUI). The MATLAB code generates simulated radar signals, mixes them with noise and manages the random generation of the parameters. The GUI simplifies the settings of the parameters and controls the dataset generation process.


# 3. Development Details
- Current development environment: MATLAB 2019b
- The tool can be compiled and the executable can run without a MATLAB license. See the section [How to run](#4-how-to-run) for more details

 # 4. How to Run
## 4.1. Run in MATLAB

* Add the following folders to MATLAB path:
    * \src\dsp\
    * \src\util\

* At the MATLAB command prompt change the current directory to \src\app\ and run appdesigner('simulatedRadarWaveformGenerator.mlapp')

* Requires the following toolboxes to run all the functionalities:
    * Signal Processing Toolbox
    * 'DSP System Toolbox'
    * 'Communications System Toolbox'
    * 'Parallel Computing Toolbox'
    * 'MATLAB Distributed Computing Server'
    * 'Phased Array System Toolbox'



## 4.2. Run from Deployed Executable
It is possible to compile an executable and run it in a machine without MATLAB installation or license. However, the licenses for MATLAB and the toolboxes are required during compilation. 
### 4.2.1. Compile from Source 
To generate an executable for the software tool:
* Use either mcc see compileSimulatedRadarWG.m, or use the MATLAB deployment tool "deploytool".
* All necessary toolboxes are required during compilation in addition to the MATLAB Compiler.
    
### 4.2.2. Prerequisites for Deployment:
For running a precompiled executable, MATLAB prerequisites for deployment must be installed. Instructions can be found in [Matlab Prerequisites](docs/Matlab_Prerequisites.txt).

# 5. Waveform Generation:
The first tab in the application is for generating waveforms. Five modulation bins are available. You can set the number of waveforms and the sampling frequency. The random waveform parameters are selected according to Table 1 in [1]. For P0N#2, the type of phase coding can also be changed.

![alt text][GUI]

[GUI]: docs/figs/SimRadarWG_GUI.PNG "Simulated radar waveform generator GUI"

After generating and saving a dataset of waveforms, we load the dataset folder in the second tab. We can set different parameters for the dataset as demonstrated in the figure below. 

![alt text][GUINoiseAdder]

[GUINoiseAdder]: docs/figs/SimRadarWG_AWGN_GUI.PNG "Simulated radar waveform generator GUI noise addition"

A reference RF dataset was generated using this software. The RF dataset is published at https://doi.org/10.18434/M32116. 
In addition a manual for using the GUI is available at [Simulated Rada Waveform Generator GUI manual](docs/Simulated_Radar_Waveform_Generator_GUI_manual.pdf). The manual contains a glossary of the parameters that are used for generation. In addition, it includes the exact parameters that were used to generate the reference RF dataset. For more information see the additional references below.

Use the data record at https://data.nist.gov/od/id/mds2-2229 to cite this work. 

# 6. References:

1.	F. H. Sanders, J. E. Carroll, G. A. Sanders, R. L. Sole, J. S. Devereux, and E. F. Drocella, “Procedures for Laboratory Testing of Environmental Sensing Capability Sensor Devices,” National Telecommunications and Information Administration, Technical Memorandum TM 18-527, Nov. 2017. Available at http://www.its.bldrdoc.gov/publications/3184.aspx.
2.	R. Caromi, M. Souryal, T. Hall “RF Dataset of Incumbent Radar Signals in the 3.5 GHz CBRS Band,” Journal of Research (NIST JRES), Volume 124, Dec. 2019, available at https://www.nist.gov/publications/rf-dataset-incumbent-radar-signals-35-ghz-cbrs-band
3.	T. Hall, R. Caromi, M. Souryal, and A. Wunderlich, "Reference Datasets for Training and Evaluating RF Signal Detection and Classification Models," in *Proc. IEEE GLOBECOM Workshop on Advancements in Spectrum Sharing*, Dec. 2019, available at https://www.nist.gov/publications/reference-data-sets-training-and-evaluating-rf-signal-detection-and-classification



