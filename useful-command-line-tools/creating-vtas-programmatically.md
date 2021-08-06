# Creating VTAs programmatically

To do so, you can check out the function`ea_genvat_wrapper`

If this is a csv file `test.csv` for the stimulation protocol:

```text
PatientID,VTALabel,Side,StimContact,Voltage
PAT101,1,L,0,1
PAT101,2,L,0,2
```

you can use:

```text
stimTable = readtable('test.csv');

rootFolder = 'XXXX';  % Parent folder of the patient folders
stimLabel = 'Test'; % Label of the stimulation

s = 1;
patientFolder = fullfile(rootFolder, stimTable.PatientID(s));
ea_genvat_wrapper(patientFolder, stimLabel, stimTable.Side{s}, stimTable.StimContact(s), stimTable.Voltage(s));
```

to create the VTAs.



