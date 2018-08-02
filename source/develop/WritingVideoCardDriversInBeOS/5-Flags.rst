标志
=======================

======================================================= =======================================================  =========== =========== =========== ===========
标志名称                                                          API 构造                                             c           s            p          A
======================================================= =======================================================  =========== =========== =========== ===========
*覆盖使用：*
B_BITMAP_WILL_OVERLAY                                       BBitmap: constructie                                     +                          +
B_BITMAP_RESERVE_OVERLAY_CHANNEL                            BBitmap: constructie
B_OVERLAY_TRANSFER_CHANNEL                                  BView: SetViewOverlay()
B_OVERLAY_MIRROR                                            BView: SetViewOverlay()
B_OVERLAY_FILTER_HORIZONTAL                                 BView: SetViewOverlay()
B_OVERLAY_FILTER_VERTICAL                                   BView: SetViewOverlay()

*模式使用：*
B_SUPPORTS_OVERLAYS                                         BScreen: struct display_mode.flags
B_HARDWARE_CURSOR                                           BScreen: struct display_mode.flags
B_IO_FB_NA                                                  BScreen: struct display_mode.flags
B_PARALLEL_ACCESS                                           BScreen: struct display_mode.flags
B_8_BIT_DAC                                                 BScreen: struct display_mode.flags
B_DPMS                                                      BScreen: struct display_mode.flags
B_SCROLL                                                    BScreen: struct display_mode.flags
B_BLANK_PEDESTAL                                            BScreen: struct display_mode.timing.flags
B_TIMING_INTERLACED                                         BScreen: struct display_mode.timing.flags
B_SYNC_ON_GREEN                                             BScreen: struct display_mode.timing.flags
B_POSITIVE_HSYNC                                            BScreen: struct display_mode.timing.flags
B_POSITIVE_VSYNC                                            BScreen: struct display_mode.timing.flags
======================================================= =======================================================  =========== =========== =========== ===========

用户覆盖标志
-----------------------------------------


B_BITMAP_WILL_OVERLAY
************************************************

B_BITMAP_RESERVE_OVERLAY_CHANNEL
************************************************

B_OVERLAY_TRANSFER_CHANNEL
************************************************

B_OVERLAY_MIRROR
************************************************

B_OVERLAY_FILTER_HORIZONTAL
************************************************

B_OVERLAY_FILTER_VERTICAL
************************************************


模式设置标志：模式标志
-----------------------------------------

B_SUPPORTS_OVERLAYS
************************************************

B_HARDWARE_CURSOR
************************************************

B_IO_FB_NA
************************************************

B_PARALLEL_ACCESS
************************************************

B_8_BIT_DAC
************************************************

B_DPMS
************************************************

B_SCROLL
************************************************

模式设置标志：模式时序标志
-----------------------------------------


B_BLANK_PEDESTAL
************************************************

B_TIMING_INTERLACED
************************************************

B_SYNC_ON_GREEN
************************************************

B_POSITIVE_HSYNC & B_POSITIVE_VSYNC
************************************************

总结
-----------------------------------------