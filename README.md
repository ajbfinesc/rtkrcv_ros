# ![rtkrcv_ros_icon](rtkrcv_ros/figures/rtkrcv_ros_icon.jpg) RTKRCV_ROS 

ROS translation of the RTKRCV - a real-time GNSS precise positioning application included in the RTKLIB package. 

New features include ROS topic publishing of output solutions. The inclusion of a new velocity output format. A new ROS service offers control over the RTK server.

![rtkrcv_ros_diagram](rtkrcv_ros/figures/rtkrcv_ros.jpg)

[RTKLIB](http://www.rtklib.com/) was originally developed by [Tomoji Takasu](https://github.com/tomojitakasu), Copyright (c) 2007-2013, T. Takasu, All rights reserved.

---

### Summary

The RTKRCV_ROS offers the following list of features:
- ROS publishing
  - New ROS topic devices to comunicate output solution streams.
  - All existing output solution formats can be published in ROS.
  - All previous output devices (TCP, files, serial,...) are still available.
  - Fully configurable outputs, as in the original RTKRCV.
  - Configuration continues to be made through the configuration file.
  - Possibility of choosing custom ROS topic and node names.
- New velocity output solution format.
- ROS service to receive control commands.
- New synchronization between rover and base observations to improve moving-baseline solutions.

For a full description of the implemented features take a look to the following paper:
    
### Paper
If you have used the RTKRCV_ROS package in your project, we would appreciate citations to the following paper:

Fulano, Sicrano, Beltrano. RTKLIB for ROS. Computational Statistics 32 (3), pp 1-15, 2019
Show BibTeX - Read on arXiv

*Thank You!*



### Version
The current version was developed based on the RTKLIB version 2.4.2 p13

### Author
António Ferreira (ajbf@inesctec.pt) - INESC TEC - Portugal 

### License
This project is distributed under the follwoing BSD 2-clause
license (http://opensource.org/licenses/BSD-2-Clause). Users are permitted to develop, produce or sell their own
non-commercial or commercial products utilizing, linking or including RTKLIB as
long as they comply with the license.

          Copyright (c) 2007-2013, T. Takasu, All rights reserved.

Redistribution and use in source and binary forms, with or without modification,
are permitted provided that the following conditions are met:

- Redistributions of source code must retain the above copyright notice, this
  list of conditions and the following disclaimer.

- Redistributions in binary form must reproduce the above copyright notice, this
  list of conditions and the following disclaimer in the documentation and/or
  other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE
LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR
CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE
GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION)
HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT
LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF
THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
