# Starting Into React

## Recap

React ist komplett auf Components aufgebaut welche HTML, CSS und JavaScript direkt inbegriffen haben. Damals gab es für jedes dieser Eigenschaften jeweils eine Datei d.h. für HTML gab es eine Datei, für CSS, sowie für JavaScript. React kombiniert alles zusammen.

## Props

- Props sind read-only Eigenschaften von Components
- Props können nur vom Parent Component geupdated werden

## States

- States werden benutzt wenn man etwas in seiner Lebzeit ändern will, wie z.B. ein Counter von Maus Klicks oder ein Modal Toggler.
- States sollte man nicht für jede Variable benutzen. Variablen die in ihrer Lebzeit nicht geändert werden können einfach mit **const** definiert werden.
- States Re-Rendern das Component und rekunstruiert sozusagen das Component wieder neu.
