- 👋 Hi, I’m @chiholeo1995
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
chiholeo1995/chiholeo1995 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
filter {
     xml {
        store_xml => "false"
        source => "Message"
        xpath => {
              "//Event/System/Provider/@Name" => "Provider_Name"
              "//Event/System/Provider/@Guid" => "Provider_Guid"
              "//Event/System/TimeCreated/@SystemTime" => "TimeCreated_SystemTime"
              "//Event/System/Execution/@ProcessID" => "Execution_ProcessID"
              "//Event/System/Execution/@ThreadID" => "Execution_ThreadID"
              "//Event/System/Security/@UserId" => "Security_UserId"
              "//Event/System/EventID/text()" => "Event_id"
              "//Event/System/Version/text()" => "version"
              "//Event/System/Level/text()" => "Level"
              "//Event/System/Task/text()" => "Task"
              "//Event/System/Opcode/text()" => "Opcode"
              "//Event/System/Keywords/text()" => "Keywords"
              "//Event/System/EventRecordID/text()" => "EventRecordID"
              "//Event/System/Channel/text()" => "Channel"
              "//Event/System/Computer/text()" => "Computer"
              "//Event/EventData/Data[@Name='RuleName']/text()" => "RuleName"
              "//Event/EventData/Data[@Name='UtcTime']/text()" => "UtcTime"
              "//Event/EventData/Data[@Name='ProcessGuid']/text()" => "ProcessGuid"
              "//Event/EventData/Data[@Name='ProcessId']/text()" => "ProcessId"
              "//Event/EventData/Data[@Name='Image']/text()" => "Image"
              "//Event/EventData/Data[@Name='User']/text()" => "User"
              "//Event/EventData/Data[@Name='FileVersion']/text()" => "FileVersion"
              "//Event/EventData/Data[@Name='Description']/text()" => "Description"
              "//Event/EventData/Data[@Name='Product']/text()" => "Product"
              "//Event/EventData/Data[@Name='Company']/text()" => "Company"
              "//Event/EventData/Data[@Name='CurrentDirectory']/text()" => "CurrentDirectory"
              "//Event/EventData/Data[@Name='LogonGuid']/text()" => "LogonGuid"
              "//Event/EventData/Data[@Name='LogonId']/text()" => "LogonId"
              "//Event/EventData/Data[@Name='TerminalSessionId']/text()" => "TerminalSessionId"
              "//Event/EventData/Data[@Name='IntegrityLevel']/text()" => "IntegrityLevel"
              "//Event/EventData/Data[@Name='Hashes']/text()" => "Hashes"
              "//Event/EventData/Data[@Name='ParentProcessGuid']/text()" => "ParentProcessGuid"
              "//Event/EventData/Data[@Name='ParentProcessId']/text()" => "ParentProcessId"
              "//Event/EventData/Data[@Name='ParentImage']/text()" => "ParentImage"
              "//Event/EventData/Data[@Name='ParentCommandLine']/text()" => "ParentCommandLine"
              "//Event/EventData/Data[@Name='ParentUser']/text()" => "ParentUser"
              "//Event/EventData/Data[@Name='CommandLine']/text()" => "CommandLine"
              "//Event/EventData/Data[@Name='OriginalFileName']/text()" => "OriginalFileName"
         }
     }
     ###### Drop multipathd error message
     if "usr/sbin/multipathd" in [Message] {
           drop { }
     }
     ###### Drop Error message
     if "sda: failed to get udev uid: Invalid argument" in [Message] {
           drop { }
     }
     if "sda: failed to get sgio uid: No such file or directory" in [Message] {
           drop { }
     }
     if "sda: failed to get sysfs uid: Invalid argument" in [Message] {
           drop { }
     }
     if "sda: add missing path" in [Message] {
           drop { }
     }
     ###### Drop _jsonparseerror
     if "_jsonparsefailure" in [tags] {
           drop { }
     }
}
"filter.conf" [readonly] 67L, 3628C                                                                                                                                                67,1          Bot
