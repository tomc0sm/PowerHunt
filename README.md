# PowerHunt


##  Usage 


```
git clone https://github.com/tomc0sm/PowerHunt.git

# create output folders 
mkdir .\Output\Persistence
mkdir .\Output\Execution

# run tests 
.\Tests\Persistence.test2.ps1
.\Tests\Execution.test.ps1
```


## Features 

### Persistence

#### T1197/Invoke-BitsJobs

MITREATT&CK : https://attack.mitre.org/techniques/T1197/

Adversaries may abuse BITS jobs to persistently execute code and perform various background tasks. Adversaries may abuse BITS to download (e.g. Ingress Tool Transfer), execute, and even clean up after running malicious code (e.g. Indicator Removal). 

<br>

Output fields: 

<br>


| CertificateHash | CertificateStoreLocation | CertificateStoreName | CertificateSubjectName | CreationTime       | CustomHeaders | Description    | DisplayName | Dynamic | ErrorCondition    | ErrorContext                                                                                                                                                                                           | ErrorContextDescription                                                                                                                                                                                          | ErrorDescription | FileList | FilesTotal | FilesTransferred | HttpMethod | InternalErrorCode | JobId                                  | JobState       | MaxDownloadTime | ModificationTime   | NotifyCmdLine | NotifyFlags             | OwnerAccount               | Priority  | ProxyBypassList | ProxyList | ProxyUsage    | RetryInterval | RetryTimeout | SecurityFlags              | TransferCompletionTime | TransferPolicy | TransferType | TransientErrorCount |
|-----------------|--------------------------|----------------------|------------------------|--------------------|---------------|----------------|-------------|---------|-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|----------|------------|------------------|------------|-------------------|----------------------------------------|----------------|----------------|--------------------|---------------|-------------------------|---------------------------|-----------|-----------------|-----------|---------------|---------------|--------------|----------------------------|-------------------------|----------------|--------------|---------------------|

 
<br>

#### T5103-ScheduledTask

 MITREATT&CK : https://attack.mitre.org/techniques/T1053/005/

Adversaries may abuse the Windows Task Scheduler to perform task scheduling for initial or recurring execution of malicious code. An adversary may use Windows Task Scheduler to execute programs at system startup or on a scheduled basis for persistence.Adversaries may also create "hidden" scheduled tasks (i.e. Hide Artifacts) that may not be visible to defender tools and manual queries used to enumerate tasks.

<br>

Datas are enriched with PEFileInfos module, analyzing the task target executable file. 

<br> 

Output fields : 

<br>

| TaskName | TaskPath | RegistrationInfo_Version | RegistrationInfo_Description | RegistrationInfo_URI | Triggers_LogonTrigger_Enabled | Triggers_CalendarTrigger_StartBoundary | Triggers_CalendarTrigger_Enabled | Triggers_CalendarTrigger_ScheduleByDay_DaysInterval | Principals_Principal_UserId | Principals_Principal_RunLevel | Settings_MultipleInstancesPolicy | Settings_DisallowStartIfOnBatteries | Settings_StopIfGoingOnBatteries | Settings_AllowHardTerminate | Settings_StartWhenAvailable | Settings_RunOnlyIfNetworkAvailable | Settings_IdleSettings_Duration | Settings_IdleSettings_WaitTimeout | Settings_IdleSettings_StopOnIdleEnd | Settings_IdleSettings_RestartOnIdle | Settings_AllowStartOnDemand | Settings_Enabled | Settings_Hidden | Settings_RunOnlyIfIdle | Settings_DisallowStartOnRemoteAppSession | Settings_UseUnifiedSchedulingEngine | Settings_WakeToRun | Settings_ExecutionTimeLimit | Settings_Priority | Actions_Exec_Command | Actions_Exec_Arguments | PEFileInfos_CompanyName | PEFileInfos_Copyright | PEFileInfos_DateCreation | PEFileInfos_DateModification | PEFileInfos_FileDescription | PEFileInfos_FileVersion | PEFileInfos_OriginalFileName | PEFileInfos_ProductName | PEFileInfos_ProductVersion | PEFileInfos_Sha1 | PEFileInfos_SignatureCertificateThumbprint | PEFileInfos_SignatureCertificateTrusted | PEFileInfos_SignatureStatus | PEFileInfos_SignatureSubject |
|----------|----------|--------------------------|-------------------------------|----------------------|-------------------------------|----------------------------------------|----------------------------------|-----------------------------------------------|-----------------------------|------------------------------|-------------------------------|-----------------------------------|---------------------------------|-----------------------------|------------------------------|-----------------------------------|-----------------------------|--------------------------------|-----------------------------|----------------------------|-------------------|----------------|---------------------|-------------------------------------|----------------------------------|------------------|--------------------------|-----------------|-------------------|--------------------|---------------------|--------------------|----------------------|------------------------|----------------------|------------------|---------------------|---------------------|-------------------|--------------------------|------------------|--------------------------------------|---------------------------------|----------------------|----------------------|

<br> 



#### T5143-Service


#### T5146-AppInitDLL


#### T5146-WMIEventSubscription


#### T5141-RegistryRunKey


#### T5147-StartupFolder


#### T5147-Winlogon


### Execution 

#### T1204-ExecEventLog

This module provides a list of 4688 events from windows Security Log and automatically enrich datas using PEFileInfo util.   Details depend on Windows Audit Policy Strategy : 

- To log all events creations :  Advanced Audit Policy Configuration ➔ System Audit Policies ➔ Detailed Tracking ➔ Audit Process Creation. Log both Audit and failure
- To log command lines : Administrative Templates ➔ System ➔  Audit Process Creation. Enable

  




