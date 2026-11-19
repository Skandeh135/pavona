# aon_timer Feature Report

## Feature List
<table class="verification_report_table">
  <thead>
    <tr>
      <th>Features</th>
      <th>Descriptions</th>
    </tr>
  </thead>
  <tbody>
    <tr id="aon_timerwakeupinterrupt">
      <td>AON_TIMER.WAKEUP.INTERRUPT</td>
      <td>The AON_TIMER block triggers interrupts when the wakeup threshold is reached.</td>
    </tr>
    <tr id="aon_timerwakeupwakeup_config">
      <td>AON_TIMER.WAKEUP.WAKEUP_CONFIG</td>
      <td>The AON_TIMER wake-up period can be configured.</td>
    </tr>
    <tr id="aon_timerwakeupwakeup_request">
      <td>AON_TIMER.WAKEUP.WAKEUP_REQUEST</td>
      <td>The AON_TIMER can wake-up the core from sleep mode.</td>
    </tr>
    <tr id="aon_timerwatchdogbark">
      <td>AON_TIMER.WATCHDOG.BARK</td>
      <td>The AON_TIMER watchdog barks if not petted in the programmed time. A bark triggers an interrupt and a wakeup.</td>
    </tr>
    <tr id="aon_timerwatchdogbite">
      <td>AON_TIMER.WATCHDOG.BITE</td>
      <td>The AON_TIMER watchdog bites if not petted in the programmed time. A bite triggers a reset.</td>
    </tr>
    <tr id="aon_timerwatchdogdisable_by_lc_ctrl">
      <td>AON_TIMER.WATCHDOG.DISABLE_BY_LC_CTRL</td>
      <td>The watchdog is disabled when the life cycle controller escalates.</td>
    </tr>
    <tr id="aon_timerwatchdoginterrupt">
      <td>AON_TIMER.WATCHDOG.INTERRUPT</td>
      <td>An interrupt is triggered when the watchdog bark threshold is reached.</td>
    </tr>
    <tr id="aon_timerwatchdogpause">
      <td>AON_TIMER.WATCHDOG.PAUSE</td>
      <td>Configure the watchdog to pause during sleep mode, resuming after wake-up.</td>
    </tr>
  </tbody>
</table>

## Feature -> Specification Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Spec Section↓ : Features→</th>
    <th>AON_TIMER.WAKEUP.WAKEUP_CONFIG</th>
    <th>AON_TIMER.WAKEUP.WAKEUP_REQUEST</th>
    <th>AON_TIMER.WAKEUP.INTERRUPT</th>
    <th>AON_TIMER.WATCHDOG.BARK</th>
    <th>AON_TIMER.WATCHDOG.BITE</th>
    <th>AON_TIMER.WATCHDOG.PAUSE</th>
    <th>AON_TIMER.WATCHDOG.DISABLE_BY_LC_CTRL</th>
    <th>AON_TIMER.WATCHDOG.INTERRUPT</th>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#theory-of-operation">Theory of Operation</a></th>
    <td></td>
    <td></td>
    <td><a href="../theory_of_operation.md#theory-of-operation">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#block-diagram">Block diagram</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="../theory_of_operation.md#design-details">Design Details</a></th>
    <td><a href="../theory_of_operation.md#design-details">X</a></td>
    <td><a href="../theory_of_operation.md#design-details">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>
</div>
</div>


## Feature -> Testpoint Matrix
<div class="feature_matrix">
<div class="table-wrapper">
<table>
  <tr>
    <th>Testpoints↓ : Features→</th>
    <th>AON_TIMER.WAKEUP.WAKEUP_CONFIG</th>
    <th>AON_TIMER.WAKEUP.WAKEUP_REQUEST</th>
    <th>AON_TIMER.WAKEUP.INTERRUPT</th>
    <th>AON_TIMER.WATCHDOG.BARK</th>
    <th>AON_TIMER.WATCHDOG.BITE</th>
    <th>AON_TIMER.WATCHDOG.PAUSE</th>
    <th>AON_TIMER.WATCHDOG.DISABLE_BY_LC_CTRL</th>
    <th>AON_TIMER.WATCHDOG.INTERRUPT</th>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#smoke">smoke</a></th>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#smoke">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#prescaler">prescaler</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#jump">jump</a></th>
    <td><a href="02_testpoint_report.md#jump">X</a></td>
    <td><a href="02_testpoint_report.md#jump">X</a></td>
    <td><a href="02_testpoint_report.md#jump">X</a></td>
    <td><a href="02_testpoint_report.md#jump">X</a></td>
    <td><a href="02_testpoint_report.md#jump">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#jump">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#stress_all">stress_all</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#max_threshold">max_threshold</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#min_threshold">min_threshold</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#wkup_count_hi_cdc">wkup_count_hi_cdc</a></th>
    <td><a href="02_testpoint_report.md#wkup_count_hi_cdc">X</a></td>
    <td><a href="02_testpoint_report.md#wkup_count_hi_cdc">X</a></td>
    <td><a href="02_testpoint_report.md#wkup_count_hi_cdc">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#custom_intr">custom_intr</a></th>
    <td><a href="02_testpoint_report.md#custom_intr">X</a></td>
    <td><a href="02_testpoint_report.md#custom_intr">X</a></td>
    <td><a href="02_testpoint_report.md#custom_intr">X</a></td>
    <td><a href="02_testpoint_report.md#custom_intr">X</a></td>
    <td><a href="02_testpoint_report.md#custom_intr">X</a></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#custom_intr">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#alternating_on_off">alternating_on_off</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aon_timer_wakeup_irq-dragonfly">chip_sw_aon_timer_wakeup_irq (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aon_timer_wakeup_irq-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aon_timer_sleep_wakeup-dragonfly">chip_sw_aon_timer_sleep_wakeup (dragonfly)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_aon_timer_sleep_wakeup-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aon_timer_sleep_wakeup-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aon_timer_wdog_bark_irq-dragonfly">chip_sw_aon_timer_wdog_bark_irq (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aon_timer_wdog_bark_irq-dragonfly">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aon_timer_wdog_bite_reset-dragonfly">chip_sw_aon_timer_wdog_bite_reset (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aon_timer_wdog_bite_reset-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aon_timer_wdog_bite_reset-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aon_timer_sleep_wdog_bite_reset-dragonfly">chip_sw_aon_timer_sleep_wdog_bite_reset (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aon_timer_sleep_wdog_bite_reset-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aon_timer_sleep_wdog_bite_reset-dragonfly">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aon_timer_sleep_wdog_sleep_pause-dragonfly">chip_sw_aon_timer_sleep_wdog_sleep_pause (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aon_timer_sleep_wdog_sleep_pause-dragonfly">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aon_timer_sleep_wdog_sleep_pause-dragonfly">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aon_timer_wdog_lc_escalate-dragonfly">chip_sw_aon_timer_wdog_lc_escalate (dragonfly)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aon_timer_wdog_lc_escalate-dragonfly">X</a></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aon_timer_wakeup_irq-egret">chip_sw_aon_timer_wakeup_irq (egret)</a></th>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aon_timer_wakeup_irq-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aon_timer_sleep_wakeup-egret">chip_sw_aon_timer_sleep_wakeup (egret)</a></th>
    <td><a href="02_testpoint_report.md#chip_sw_aon_timer_sleep_wakeup-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aon_timer_sleep_wakeup-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aon_timer_wdog_bark_irq-egret">chip_sw_aon_timer_wdog_bark_irq (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aon_timer_wdog_bark_irq-egret">X</a></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aon_timer_wdog_bite_reset-egret">chip_sw_aon_timer_wdog_bite_reset (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aon_timer_wdog_bite_reset-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aon_timer_wdog_bite_reset-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aon_timer_sleep_wdog_bite_reset-egret">chip_sw_aon_timer_sleep_wdog_bite_reset (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aon_timer_sleep_wdog_bite_reset-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aon_timer_sleep_wdog_bite_reset-egret">X</a></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aon_timer_sleep_wdog_sleep_pause-egret">chip_sw_aon_timer_sleep_wdog_sleep_pause (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aon_timer_sleep_wdog_sleep_pause-egret">X</a></td>
    <td><a href="02_testpoint_report.md#chip_sw_aon_timer_sleep_wdog_sleep_pause-egret">X</a></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th><a href="02_testpoint_report.md#chip_sw_aon_timer_wdog_lc_escalate-egret">chip_sw_aon_timer_wdog_lc_escalate (egret)</a></th>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><a href="02_testpoint_report.md#chip_sw_aon_timer_wdog_lc_escalate-egret">X</a></td>
    <td></td>
  </tr>
</table>
</div>
</div>
