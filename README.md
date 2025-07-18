# FDM Object Adder

This tool helps in bulk creation of URL and Network objects in Cisco Firepower Device Manager (FDM) through its REST API. A bulk object creation utility is usually a requirement to avoid manual GUI-based object creation which is time-consuming and error-prone when dealing with multiple objects.

**Technology Stack:** Python 3.x, Cisco FDM REST API  
**Status:** Production Ready - v1.0

## Use Case Description

The tool is developed to address the concern of bulk creation of URL and Network objects in Cisco Firepower Device Manager (FDM). Network administrators often need to add multiple URL and network objects to FDM for policy enforcement and traffic management. Manually creating these objects through the GUI is time-consuming and error-prone, especially when dealing with dozens or hundreds of objects.

This tool solves that problem by:
- **Automating bulk object creation** from simple text files
- **Reducing manual errors** through programmatic creation
- **Saving time** by processing multiple objects in seconds
- **Providing clear feedback** on success/failure for each object

**Benefits:**
- Reduces object creation time from hours to minutes
- Ensures consistency in object naming conventions
- Provides audit trail through console output
- Supports both URL and Network object types

## Installation

Requirements for installation:

```
pip3 install requests
pip3 install urllib3
```

Or alternatively you can use the command below to download dependencies via the requirements.txt file, this has to be executed from the downloaded script directory:

```
pip3 install -r requirements.txt
```

### Prerequisites
- Python 3.6 or higher
- Cisco FDM with REST API access
- Network connectivity to FDM management interface

### File Structure
```
FDM Object Adder/
├── fdm_object_adder.py # Main script
├── url.txt             # URL objects to create
├── ip.txt              # IP/Network objects to create
├── requirements.txt    # Python dependencies
├── fdm/                # Virtual environment (if using)
└── README.md           # This file
```

## Configuration

### Input Files

Create two text files in the same directory as the script:

1. **url.txt** - One URL per line:
   ```
   google.com
   facebook.com
   github.com
   ```

2. **ip.txt** - One IP address per line:
   ```
   192.168.1.100
   10.0.0.50
   172.16.1.25
   ```

### FDM Requirements
- FDM must be accessible via HTTPS
- Valid username/password credentials
- Appropriate permissions to create network objects

## Usage

Once the dependencies are installed and the code is pulled from GitHub, it is good to go. Below mentioned are the steps to follow in order to execute it:

1. **First thing to ensure is**, the machine where the code will be installed should have connectivity with the FDM under concern.
2. **It is recommended to create a different user** for the tool, so that it does not block existing users from logging into the FDM for operational changes.
3. **Navigate to the location** where the script is installed.

### Prepare your input files:

Create two text files in the same directory as the script:

1. **url.txt** - One URL per line:
   ```
   google.com
   facebook.com
   github.com
   ```

2. **ip.txt** - One IP address per line:
   ```
   192.168.1.100
   10.0.0.50
   172.16.1.25
   ```

### Execute the script:

In order to execute the script, run the below command:

```bash
python3 fdm_object_adder.py
```

Once the script is executed, you will be prompted to enter FDM connection details:

```
FDM IP: 192.168.1.10
Username: admin
Password: [hidden]
```

### Monitor the output:

Once the credentials are entered, the script connects to the FDM and processes the input files:

```
============================================================
║                                                          ║
║                  FDM Object Adder                        ║
║                                                          ║
║  • Creates URL objects from url.txt                      ║
║  • Creates Network objects from ip.txt                   ║
║                                                          ║
============================================================

Authentication successful

Processing url.txt: 5 URLs
SUCCESS: google_com
SUCCESS: facebook_com
SUCCESS: github_com

Processing ip.txt: 3 IPs
SUCCESS: Host_192_168_1_100
SUCCESS: Host_10_0_0_50
SUCCESS: Host_172_16_1_25

Completed: 8 objects created
```

### Output Generated:

1. **Console output** displays the progress of object creation in real-time
2. **Success/Failure status** for each object with specific error messages if any
3. **Total count** of successfully created objects at the end
4. **Object names** are automatically sanitized for FDM compatibility

## Object Naming Convention

The script automatically sanitizes names to ensure FDM compatibility:

- **URL Objects:** Domain names with special characters replaced by underscores
  - `google.com` → `google_com`
  - `sub.domain.com` → `sub_domain_com`

- **Network Objects:** IP addresses with dots replaced by underscores and "Host_" prefix
  - `192.168.1.100` → `Host_192_168_1_100`
  - `10.0.0.50` → `Host_10_0_0_50`

## Known Issues

Currently the tool supports basic URL and Network object creation. The below fields/features are not supported currently:

1. **Port Objects:** Only URL and Network objects are supported
2. **Object Groups:** Individual objects only, no group creation
3. **Multi-domain deployments:** Single domain support only
4. **FQDN objects:** Only URL objects are supported

- **SSL Warnings:** The script disables SSL verification for self-signed certificates. This is expected behavior for most FDM deployments.
- **Duplicate Objects:** If objects with the same name already exist, the creation will fail for those specific objects.

## Roadmap

The next version of the tool/utility will have the following items included:

1. Support for Port objects creation
2. Object Groups creation capability  
3. FQDN network objects support

If you encounter issues:

1. **Check the console output** for specific error messages
2. **Verify FDM connectivity** by accessing the web interface
3. **Confirm file format** - ensure one entry per line in text files

## Security Considerations

- **Credentials:** The script prompts for passwords securely and doesn't store them
- **HTTPS:** All API communication uses HTTPS encryption
- **Input Validation:** URLs and IP addresses are sanitized before processing
- **Error Handling:** Sensitive information is not exposed in error messages

## Requirements

- Python 3.6+
- requests library
- urllib3 library
- Cisco FDM 7.2+ (tested versions)
- Network access to FDM management interface

## Author(s)

This project was written and is maintained by the following individuals:

• **Anvesh Pathak** - [anvpatha@cisco.com](mailto:anvpatha@cisco.com)

## Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for:
- Bug fixes
- Feature enhancements
- Documentation improvements
- Additional object types support

## License

This project is licensed under the MIT License. See LICENSE file for details.

## Credits and References

- **Cisco FDM REST API Documentation:** Official API reference
- **Python Requests Library:** HTTP library for API communication
- **Cisco DevNet:** Development resources and sandboxes for testing

---

*This tool is designed to work with Cisco Firepower Device Manager and has been tested with FDM versions 7.2 and above.*
