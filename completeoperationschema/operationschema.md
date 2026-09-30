| ID | Precondition | Events/Inputs | Post-condition |
| --- | --- | --- | --- |
| OP01 | System is powered on. | Power-on event; sensor and control-device status signals. | All essential sensors OK: system enters MONITORING mode. Otherwise conservation stays blocked and the fault is reported. |
| OP02 | Self-check passed; artifact placed inside the chamber; artifact identification and limits are available. | Artifact placed; artifact ID; required temperature and humidity limits. | Artifact ID and environmental profile are stored; monitoring of the artifact begins. |
| OP03 | Self-check passed (system in MONITORING or a later active mode). | Periodic readings: temperature, humidity, light, vibration, door status, power availability. | Latest sensor values are available to all other operations. |
| OP04 | Artifact profile is loaded; door is closed; no vibration or protection response active. | Door-closed signal; profile-loaded flag. | System enters CONSERVATION_ACTIVE mode. If the door is open, monitoring continues and conservation is not started. |
| OP05 | CONSERVATION_ACTIVE; valid temperature and humidity readings. | Temperature and humidity readings; artifact's permitted ranges. | Each value is marked in range or out of range; a correction request is raised for any out-of-range value. |
| OP06 | A value is out of range; door closed; recovery period not expired. | Out-of-range result; correction command to heating/cooling or humidity control. | Correction command issued and recovery timer started; the artifact is NOT yet declared safe. |
| OP07 | Correction command issued; recovery timer running. | New sensor readings; recovery timer value. | Value back in range within the period: normal conservation continues. Value still out of range at timeout: protection response is triggered. |
| OP08 | Condition not corrected within the recovery period. | Recovery-timeout event. | System enters PROTECTION_MODE; light exposure is reduced and extra environmental controls are active. |
| OP09 | Protection response has started (or another abnormal condition needs operator attention). | Protection-mode trigger event. | Alert is generated and sent to the museum operator. |
| OP10 | Artifact is inside the chamber; vibration sensor working. | Vibration reading above the permitted threshold. | Risky activities are suspended; system enters VIBRATION_RESPONSE; stabilization timer starts. |
| OP11 | System is in VIBRATION_RESPONSE. | Vibration readings; stabilization timer. | Vibration below threshold for the full period: return to conservation is allowed. If it rises again, the timer restarts and the system stays in VIBRATION_RESPONSE. |
| OP12 | CONSERVATION_ACTIVE; artifact inside. | Door-opened signal. | Normal conservation activities stop immediately; only monitoring continues while the door is open. |
| OP13 | Door has been closed again after being open. | Door-closed signal; current sensor and environmental readings. | All sensors OK and conditions in range: conservation resumes. Otherwise the system stays suspended or goes to correction or protection. |
| OP14 | Main power lost while an artifact is in conservation; emergency power source is available. | Power-loss signal; emergency-power-available signal. | System runs on emergency power and continues monitoring and protecting the artifact. |
| OP15 | Main power lost and emergency power is unavailable. | Power-loss signal; emergency-power-unavailable signal. | Incident is recorded and the system is in the safe shutdown state. |
| OP16 | Operator requests removal; chamber is in a safe condition; no protection response is underway. | Operator removal request; system safety status. | Removal is authorized and the artifact is taken out. If conditions are unsafe, the request is denied. |

