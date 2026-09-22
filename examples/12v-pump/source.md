# Synthetic service note — auxiliary circulation pump P1

**Document ID:** DDS-EX-PUMP-001  
**Revision:** 1.0  
**Status:** synthetic DDS reference material

## Circuit description

The auxiliary circulation pump **P1** operates from a nominal 12 V electrical system.

Battery supply reaches fuse **F27**, rated at **15 A**. F27 supplies terminal **30** of relay **K3**. When K3 is energised, terminal 30 is connected to terminal **87**, which supplies the positive terminal of P1.

The negative terminal of P1 connects to chassis ground point **G104**.

K3 terminal **86** receives ignition-switched positive voltage. K3 terminal **85** is controlled to ground by the ECU. When the ECU commands the circulation pump on, it grounds terminal 85, energising K3.

## Expected values

With the pump commanded on and the electrical system operating normally:

| Measurement | Expected value |
| --- | --- |
| F27 continuity | closed / approximately 0 Ω |
| Voltage at K3 terminal 30 to ground | 11.5–14.8 V |
| Voltage at K3 terminal 87 to ground, relay energised | 11.5–14.8 V |
| Voltage across P1, pump commanded on | 11.5–14.8 V |
| G104 voltage drop to battery negative under load | < 0.5 V |

## Diagnostic procedure — pump does not run

1. Confirm that the pump has been commanded on.
2. Inspect F27 and verify continuity.
3. With the pump commanded on, measure voltage across P1.
4. If **11.5–14.8 V is present across P1 but P1 does not run**, inspect the P1 connector, verify the G104 ground path under load, and test P1.
5. If **less than 11.5 V is present across P1**, measure K3 terminal 87 to ground while the relay is commanded on.
6. If K3 terminal 87 is within 11.5–14.8 V but P1 supply is low, inspect the wiring between K3 terminal 87 and P1.
7. If K3 terminal 87 is low, verify supply at K3 terminal 30. If terminal 30 has correct supply, test relay K3 and its control circuit. If terminal 30 is also low, inspect F27 and the upstream supply.

## Notes

Do not infer relay or pump failure solely from an audible click. Use the measurements above to isolate the fault.
