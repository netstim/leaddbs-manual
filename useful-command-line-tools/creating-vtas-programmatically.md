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

for s=1:size(stimTable,1)
    patientFolder = fullfile(rootFolder, stimTable.PatientID(s));

    ea_genvat_wrapper(patientFolder, stimLabel, stimTable.Side{s}, stimTable.StimContact(s), stimTable.Voltage(s));

    nativeStimFolder = fullfile(patientFolder, 'stimulations', ea_nt(1), stimLabel);
    templateStimFolder = fullfile(patientFolder, 'stimulations', ea_nt(0), stimLabel);
    VTANative = ea_regexpdir(nativeStimFolder, '^vat_.*(left|right)\.', 0);
    VTATemplate = ea_regexpdir(templateStimFolder, '^vat_.*(left|right)\.', 0);
    VTA = [VTANative; VTATemplate];
    VTARenamed = replace(VTA, {'right','left'}, num2str(stimTable.VTALabel(s)));
    cellfun(@(x,y) movefile(x,y), VTA, VTARenamed);
end
```

to create the VTAs.



