ThinkPad Helix 2ndのベンチマークをとってみたらX220とかSurface Pro 2と同じぐらいだった
#######################################################################################

:date: 2015-03-14 15:00:17
:modified: 2016-06-06 22:54:42
:category: Hardware/ノートPC
:tags: ThinkPad Helix
:slug: helix-benchmark
:authors: M\. Tsuyuki

.. tags: bash, bash, screen, cygwin, bash, zsh, cygwin, Firefox, keyboard, math, pelican, Pelican, percol, python, python, reStructuredText, Vimperator, TODO, Vim, Vimperator, yoga_tablet2, zsh
.. category: blog, PC, Software, Software/Blog, Software/CUI

2月にThinkpad Helix 2nd genを購入してからしばらく経つ。なんだか，私以外にほとんど誰も買っていなさそうなのでベンチマーク結果を書いておこう。ちなみに，ベンチマークはトリプルディスプレイで，FirefoxとかThunderBirdみたいなプログラムを起動したまま測定しているので，普段使いの環境で最低でもこれぐらいの性能はでるよという意味だと思ってほしい。

一番気になっているのはCore M 5Y71の性能なのだが，いろいろ比べてみるとSurface Pro 2やThinkPad X220と大体同じ程度のようだ。

.. PELICAN_END_SUMMARY

環境
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

まずは環境について。私が購入したのは

- Intel Core M-5Y71 CPU @ 1.20GHz
- SSDが128GB
- デジタイザー付き
- キーボードはバッテリー＆トラックポイント内蔵の Ultrabook Pro Keyboard

な個体。

CrystaldDiskInfo
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Crystaldiskinfo を見てみると，SSDはSAMSUNGのMZNTE128HMGR-000L1とわかる。

.. code::

    ----------------------------------------------------------------------------
    CrystalDiskInfo 6.3.0 (C) 2008-2015 hiyohiyo
                                    Crystal Dew World : http://crystalmark.info/
    ----------------------------------------------------------------------------

        OS : Windows 8.1  [6.3 Build 9600] (x64)
      Date : 2015/03/14 14:34:50

    -- Controller Map ----------------------------------------------------------
     + Intel(R) 9 Series Chipset Family SATA AHCI Controller [ATA]
       - SAMSUNG MZNTE128HMGR-000L1

    ----------------------------------------------------------------------------
               Model : SAMSUNG MZNTE128HMGR-000L1
            Firmware : EXT26L0Q
       Serial Number : **************
           Disk Size : 128.0 GB (8.4/128.0/128.0/128.0)
         Buffer Size : 不明
         Queue Depth : 32
        # of Sectors : 250069680
       Rotation Rate : ---- (SSD)
           Interface : Serial ATA
       Major Version : ACS-2
       Minor Version : ATA8-ACS version 4c
       Transfer Mode : SATA/600 | SATA/600
      Power On Hours : 106 時間
      Power On Count : 138 回
    Wear Level Count : 7
         Temperature : 33 C (91 F)
       Health Status : 正常 (100 %)
            Features : S.M.A.R.T., 48bit LBA, NCQ, TRIM, DevSleep
           APM Level : ----
           AAM Level : ----

CrystalDiskMark
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

SSDはSAMSUNG製とわかったので，ベンチマークをとってみる。まあまあというところか。

.. figure:: {static}/images/Helix_CrystalDiskMark.png
    :alt: Helix 2nd GenのCrystalDiskMark

    Helix 2nd GenのCrystalDiskMark

.. code::

    -----------------------------------------------------------------------
    CrystalDiskMark 3.0.3 x64 (C) 2007-2013 hiyohiyo
                               Crystal Dew World : http://crystalmark.info/
    -----------------------------------------------------------------------
    * MB/s = 1,000,000 byte/s [SATA/300 = 300,000,000 byte/s]

               Sequential Read :   432.759 MB/s
              Sequential Write :   125.128 MB/s
             Random Read 512KB :   375.921 MB/s
            Random Write 512KB :   118.326 MB/s
        Random Read 4KB (QD=1) :    30.766 MB/s [  7511.2 IOPS]
       Random Write 4KB (QD=1) :    54.359 MB/s [ 13271.2 IOPS]
       Random Read 4KB (QD=32) :   227.219 MB/s [ 55473.5 IOPS]
      Random Write 4KB (QD=32) :   115.257 MB/s [ 28139.0 IOPS]

      Test : 1000 MB [C: 51.6% (54.7/106.0 GB)] (x3)
      Date : 2015/03/14 14:57:34
        OS : Windows 8.1  [6.3 Build 9600] (x64)

Super PI
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

CPUの速度もみておこう。シングルスレッドの速度しか見れないが，伝統的に重要なSuper PIの実行結果は以下のとおり。

.. code::

    ThinkPad Helix 2nd Gen Core M 5Y71 @ 1.2GHz

    Super PI
    00分 06秒 52万桁
    00分 13秒 104万桁
    00分 34秒 209万桁
    01分 52秒 419万桁
    05分 17秒 838万桁

比較のために104万桁の結果をぐぐってみた。一見するとだいたいX201以上X220以下に思えるが，実は最近のThinkPadのCPUではシングルスレッドの性能は頭打ちでCore Mの13秒ってのは十分に早いとわかる。むしろ，最大1.4GHzのくせに13秒ってのはかなりすごかったりするのではないだろうか。特に設定をいじってはいなのだが，自動的に2.9GHzまでTurbo Boostが効いているのかもしれない。

.. code::

    Super PI 104万桁
    ThinkPad X60   Core2 Duo T5600 @ 1.83GHz     32秒
    ThinkPad X61   Core2 Duo T7300 @ 2.0GHz      26秒
    ThinkPad X200  Core2 Duo P8400 @ 2.66GHz     22秒
    ThinkPad X201s Core i7 840LM                 18秒
    ThinkPad X201  Core i7 620M    @ 2.66GHz     14秒
    ThinkPad X220i Core i3 2310M   @ 2.10GHz     19秒
    ThinkPad X220  Core i7 2640M   @ 2.8GHz      11秒
    Thinkpad X230  Core i3 3110M                 16秒
    ThinkPad X230  Core i5 3360M                 11秒
    ThinkPad X240s Core i7 4500U                 12秒
    ThinkPad X240  Core i3 4030U   @ 1.90GHz     19秒

Windows 8.1 のエクスペリエンスインデックス
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Windows 8.1 のエクスペリエンスインデックス(WinSat)の値は以下のとおり。これは大した比較対象がないので良くわからない。

.. code::

    プロセッサ：                 7.1
    メモリ（RAM）：              7.5
    グラフィックス：             5.7
    ゲーム用グラフィックス：     5
    プライマリ ハードディスク：  7.95

CrystalMark 2004R3
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

CrystalMark 2004R3の結果は以下のとおり。

.. figure:: {static}/images/crystalmark_3.png
    :alt: Helix 2nd GenのCrystalMark 2004R3

    Helix 2nd GenのCrystalMark 2004R3

.. code::

    -=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
    CrystalMark 2004R3 [0.9.126.452] (C) 2001-2008 hiyohiyo
                                      Crystal Dew World [http://crystalmark.info/]
    -=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=

    ------------------------------------------------------------------------------
    CrystalMark Result
    ------------------------------------------------------------------------------

        CrystalMark :  171695

    [ ALU ]             37303
          Fibonacci :   13657
          Napierian :   11115
       Eratosthenes :    5209
          QuickSort :    7300
    [ FPU ]             33333
            MikoFPU :    5032
         RandMeanSS :   16780
                FFT :    6359
         Mandelbrot :    5140
    [ MEM ]             40970
               Read : 17394.68 MB/s ( 17394)
              Write : 8895.32 MB/s (  8895)
         Read/Write : 8183.10 MB/s (  8183)
              Cache : 64768.35 MB/s (  6476)
    [ HDD ]             32830
               Read :  382.79 MB/s (  7413)
              Write :  121.90 MB/s (  4438)
     RandomRead512K :  294.87 MB/s (  6948)
    RandomWrite512K :  122.75 MB/s (  4455)
     RandomRead 64K :  164.29 MB/s (  5285)
    RandomWrite 64K :  114.58 MB/s (  4291)
    [ GDI ]             14228
               Text :    6490
             Square :    1231
             Circle :    3278
             BitBlt :    3229
    [ D2D ]              4437
       Sprite    10 :  332.40 FPS  (    33)
       Sprite   100 :  219.51 FPS  (   219)
       Sprite   500 :  123.92 FPS  (   619)
       Sprite  1000 :   85.14 FPS  (   851)
       Sprite  5000 :   26.12 FPS  (  1306)
       Sprite 10000 :   14.09 FPS  (  1409)
    [ OGL ]              8594
      Scene 1 Score :    5566
      Lines (x1000) : ( 939318)
      Scene 1  CPUs : (    128)
      Scene 2 Score :    3028
    Polygons(x1000) : ( 149190)
      Scene 2  CPUs : (     64)

    ------------------------------------------------------------------------------
    System Information
    ------------------------------------------------------------------------------
                 OS : Windows NT6.2 Home Premium  [6.2 Build 9200]
       Display Mode : 1920 x 1080 32bit 60Hz
             Memory : 8091 MB
            DirectX : 11.0
    ------------------------------------------------------------------------------
    CPU
    ------------------------------------------------------------------------------
           CPU Name : Intel
      Vendor String : GenuineIntel
        Name String : Intel(R) Core(TM) M-5Y71 CPU @ 1.20GHz
           CPU Type : Original OEM processor
    Number(Logical) : 4
             Family : 6
              Model : D
           Stepping : 4
            Feature : MMX SSE SSE2 SSE3 SSSE3 SSE4.1 SSE4.2 XD VT Intel 64
              Clock : 1396.76 MHz
          Data Rate :    QDR

比較のために他機種のスコアをググって，一覧表にまとめると以下のようになる。なお，Helix 2ndの2.9GHzの値は `Surface Pro 3の発熱抑制法を探る：「Turbo Boost無効化」と「クロック上限の設定」を試す - Surface Pro 3 ビジネス活用日記 <http://surface.viva-m-tablet.info/entry/2014/08/31/010157>`_ にあるやり方にしたがって Turbo Boostを有効化したときの値である。

こうして値を比較してみると，やはり Helix 2nd GenのCore M 5Y71は大体X220相当のCPU性能とわかる。一方，CPU内蔵のグラフィック機能は大きく向上している。

.. csv-table:: CrystalMark 2004R3のスコア一覧
   :header:  "","Helix 2nd", "Helix 2nd", "X61", "X201", "X220i", "X220", "X230", "X230"

    "CPU", "Core M 5Y71", "Core M5Y71", "Core2Duo T8100", "Core i5 540M ", "Core i3 330M", "Core i5 2520M", "Core i5 3210M", "Core i7 3520M"
    "Freq", 1.2GHz, 2.9GHz, 2.10GHz, "", 2.13GHz, 2.50GHz, "",""
    "Mark", 123201, 171695, 90308, 108364, 89793, 167737, 154895, 224930
    "ALU", 21582, 37303, 20741, 33927, 26277, 35549, 44238, 54111
    "FPU", 21044, 33333, 18990, 34884, 26464, 36948, 44797, 52647
    "MEM", 27659, 40970, 11282, 19402, 17454, 34609, 28567, 49300
    "HDD", 33204, 32830, 29406, 7702, 9142, 43195, 12655, 37676
    "GDI", 8534, 14228, 6413, 8315, 7223, 11930, 14839, 19092
    "D2D", 4505, 4437, 1640, 1823, 1442, 1962, 2374, 2963
    "OGL", 6673, 8594, 1836, 2311, 1791, 3544, 7425, 9141

ちなみにSurfaceシリーズのスコアと比較すると以下のとおり。ちゃんとTurbo Boostを効かせれば，Helix 2ndはSurface ProやSurface Pro 2並の性能といえる。

.. csv-table:: CrystalMark 2004R3のスコア一覧
   :header:  "","Helix 2nd", "Helix 2nd",   `Surface Pro <http://unwire.hk/2013/03/18/microsoft-surface-pro-trial-few-days-comment/notebook/>`_ , `Surface Pro 2 <http://pc.watch.impress.co.jp/docs/column/nishikawa/20131028_621158.html>`_ ,  `Surface Pro 3 <http://d.hatena.ne.jp/baba-p/20140724/p2>`_

    "CPU", "Core M 5Y71", "Core M5Y71", "Core i5 3317U", "Core i5 4200U", "Core i7 4650U"
    "Freq", 1.2GHz, 2.9GHz, 1.7GHz-2.6GHz, 1.6GHz-2.6GHz, 1.7GHz-3.3GHz
    "Mark", 123201, 171695, 168121, 188945, 200396
    "ALU", 21582, 37303, 38276, 37568, 45765
    "FPU", 21044, 33333, 36208, 36385, 42511
    "MEM", 27659, 40970, 39592, 41894, 45835
    "HDD", 33204, 32830, 32554, 39513, 35499
    "GDI", 8534, 14228, 14202, 15074, 15815
    "D2D", 4505, 4437, 1917, 7373, 4524
    "OGL", 6673, 8594, 5372, 11138, 10477

CPU-Z
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

もうちょっと詳細なハードウェア情報を知りたい場合のために，CPU-Zの出力する情報も置いておこう。

.. code::

    CPU-Z TXT Report
    -------------------------------------------------------------------------

    Binaries
    -------------------------------------------------------------------------
    CPU-Z version			1.72.0.x64

    Processors
    -------------------------------------------------------------------------
    Number of processors		1
    Number of threads		4

    APICs
    -------------------------------------------------------------------------
    Processor 0
        -- Core 0
            -- Thread 0	0
            -- Thread 1	1
        -- Core 1
            -- Thread 0	2
            -- Thread 1	3

    Timers
    -------------------------------------------------------------------------
        ACPI timer		3.580 MHz
        HPET timer		14.318 MHz
        Perf timer		1.364 MHz
        Sys timer		1.000 KHz

    Processors Information
    -------------------------------------------------------------------------
    Processor 1			ID = 0
        Number of cores		2 (max 8)
        Number of threads	4 (max 16)
        Name			Intel Core M
        Codename		Broadwell-Y
        Specification		Intel(R) Core(TM) M-5Y71 CPU @ 1.20GHz
        Package (platform ID)	Socket 1234 FCBGA (0x7)
        CPUID			6.D.4
        Extended CPUID		6.3D
        Core Stepping		E0/F0
        Technology		14 nm
        TDP Limit		4.5 Watts
        Tjmax			95.0 ｰC
        Core Speed		1396.7 MHz
        Multiplier x Bus Speed	14.0 x 99.8 MHz
        Stock frequency		1400 MHz
        Instructions sets	MMX, SSE, SSE2, SSE3, SSSE3, SSE4.1, SSE4.2, EM64T, VT-x, AES, AVX, AVX2, FMA3, TSX
        L1 Data cache		2 x 32 KBytes, 8-way set associative, 64-byte line size
        L1 Instruction cache	2 x 32 KBytes, 8-way set associative, 64-byte line size
        L2 cache		2 x 256 KBytes, 8-way set associative, 64-byte line size
        L3 cache		4 MBytes, 16-way set associative, 64-byte line size
        FID/VID Control		yes

        Turbo Mode		supported, enabled
        Max non-turbo ratio	14x
        Max turbo ratio		29x
        Max efficiency ratio	5x
        O/C bins		none
        Ratio 1 core		29x
        Ratio 2 cores		26x
        Ratio 3 cores		26x
        Ratio 4 cores		26x
        Ratio 5 cores		26x
        Ratio 6 cores		26x
        TSC			1397.3 MHz
        TSC_24			24.0 MHz
        APERF			2442.0 MHz
        MPERF			1369.4 MHz
        IA Voltage Mode		PCU adaptive
        IA Voltage Offset	0 mV
        GT Voltage Mode		PCU adaptive
        GT Voltage Offset	0 mV
        LLC/Ring Voltage Mode	PCU adaptive
        LLC/Ring Voltage Offset	0 mV
        Agent Voltage Mode	PCU adaptive
        Agent Voltage Offset	0 mV

    Thread dumps
    -------------------------------------------------------------------------
    CPU Thread 0
        APIC ID			0
        Topology		Processor ID 0, Core ID 0, Thread ID 0
        Type			01020209h
        Max CPUID level		00000014h
        Max CPUID ext. level	80000008h
        Cache descriptor	Level 1, D, 32 KB, 2 thread(s)
        Cache descriptor	Level 1, I, 32 KB, 2 thread(s)
        Cache descriptor	Level 2, U, 256 KB, 2 thread(s)
        Cache descriptor	Level 3, U, 4 MB, 16 thread(s)

    CPU Thread 1
        APIC ID			1
        Topology		Processor ID 0, Core ID 0, Thread ID 1
        Type			01020209h
        Max CPUID level		00000014h
        Max CPUID ext. level	80000008h
        Cache descriptor	Level 1, D, 32 KB, 2 thread(s)
        Cache descriptor	Level 1, I, 32 KB, 2 thread(s)
        Cache descriptor	Level 2, U, 256 KB, 2 thread(s)
        Cache descriptor	Level 3, U, 4 MB, 16 thread(s)

    CPU Thread 2
        APIC ID			2
        Topology		Processor ID 0, Core ID 1, Thread ID 0
        Type			01020209h
        Max CPUID level		00000014h
        Max CPUID ext. level	80000008h
        Cache descriptor	Level 1, D, 32 KB, 2 thread(s)
        Cache descriptor	Level 1, I, 32 KB, 2 thread(s)
        Cache descriptor	Level 2, U, 256 KB, 2 thread(s)
        Cache descriptor	Level 3, U, 4 MB, 16 thread(s)

    CPU Thread 3
        APIC ID			3
        Topology		Processor ID 0, Core ID 1, Thread ID 1
        Type			01020209h
        Max CPUID level		00000014h
        Max CPUID ext. level	80000008h
        Cache descriptor	Level 1, D, 32 KB, 2 thread(s)
        Cache descriptor	Level 1, I, 32 KB, 2 thread(s)
        Cache descriptor	Level 2, U, 256 KB, 2 thread(s)
        Cache descriptor	Level 3, U, 4 MB, 16 thread(s)

    Chipset
    -------------------------------------------------------------------------
    Northbridge			Intel Broadwell-U rev. 09
    Southbridge			Intel Broadwell-Y PCH rev. 03
    Memory Type			DDR3
    Memory Size			8092 MBytes
    Channels			Dual
    Memory Frequency		798.1 MHz (1:6)
    CAS# latency (CL)		12.0
    RAS# to CAS# delay (tRCD)	15
    RAS# Precharge (tRP)		15
    Cycle Time (tRAS)		34
    Row Refresh Cycle Time (tRFC)	104
    Command Rate (CR)		1T
    Uncore Frequency		1596.8 MHz
    MCHBAR I/O Base address		0x0FED10000
    MCHBAR I/O Size			19456
    MCHBAR registers

    Memory SPD
    -------------------------------------------------------------------------

    Monitoring
    -------------------------------------------------------------------------
    Mainboard Model		20CGCTO1WW (0x000002B1 - 0x11B04D98)

    LPCIO
    -------------------------------------------------------------------------
    LPCIO Vendor		SMSC
    LPCIO Vendor ID		0x55
    LPCIO Chip ID		0x19
    Config Mode I/O address	0x4E
    Config Mode LDN		0xC
    Register space		class = 0x8, base address = 0x01610

    Hardware Monitors
    -------------------------------------------------------------------------
    Hardware monitor	ACPI
        Temperature 0	49ｰC (120ｰF) [0xC96] (THM0)

    Hardware monitor	Battery
        Voltage 0	8.35 Volts [0x20A1] (Current Voltage)
        Capacity 0	35170 mWh [0x8962] (Designed Capacity)
        Capacity 1	35030 mWh [0x88D6] (Full Charge Capacity)
        Capacity 2	34960 mWh [0x8890] (Current Capacity)
        Level 0		1 pc [0x63] (Wear Level)
        Level 1		100 pc [0x63] (Charge Level)

    Hardware monitor	Battery
        Voltage 0	8.33 Volts [0x2088] (Current Voltage)
        Capacity 0	26170 mWh [0x663A] (Designed Capacity)
        Capacity 1	26540 mWh [0x67AC] (Full Charge Capacity)
        Capacity 2	26540 mWh [0x67AC] (Current Capacity)
        Level 0		n.a. [0x64] (Wear Level)
        Level 1		100 pc [0x64] (Charge Level)

    PCI Devices
    -------------------------------------------------------------------------
    Description			Host Bridge
    Location			bus 0 (0x00), device 0 (0x00), function 0 (0x00)
    Common header
        Vendor ID		0x8086
        Model ID		0x1604
        Revision ID		0x09
        PI			0x00
        SubClass		0x00
        BaseClass		0x06
        Cache Line		0x00
        Latency			0x00
        Header			0x00
    PCI header
        Subvendor ID		0x17AA
        Subsystem ID		0x222B
        Int. Line		0x00
        Int. Pin		0x00
    PCI capability
        Caps class		Vendor Dependant
        Caps offset		0xE0

    Description			VGA Controller
    Location			bus 0 (0x00), device 2 (0x02), function 0 (0x00)
    Common header
        Vendor ID		0x8086
        Model ID		0x161E
        Revision ID		0x09
        PI			0x00
        SubClass		0x00
        BaseClass		0x03
        Cache Line		0x00
        Latency			0x00
        Header			0x00
    PCI header
        Address 0 (memory)	0xF0000000
        Address 2 (memory)	0xE0000000
        Address 4 (port)	0x0000FFC0
        Subvendor ID		0x17AA
        Subsystem ID		0x222B
        Int. Line		0x00
        Int. Pin		0x01
    PCI capability
        Caps class		Message Signalled Interrupts
        Caps offset		0x90
    PCI capability
        Caps class		Power Management
        Caps offset		0xD0
        Caps version		1.1
    PCI capability
        Caps class		0x13
        Caps offset		0xA4

    Description			Multimedia device
    Location			bus 0 (0x00), device 3 (0x03), function 0 (0x00)
    Common header
        Vendor ID		0x8086
        Model ID		0x160C
        Revision ID		0x09
        PI			0x00
        SubClass		0x03
        BaseClass		0x04
        Cache Line		0x10
        Latency			0x00
        Header			0x00
    PCI header
        Address 0 (memory)	0xF1118000
        Subvendor ID		0x17AA
        Subsystem ID		0x222B
        Int. Line		0x10
        Int. Pin		0x01
    PCI capability
        Caps class		Power Management
        Caps offset		0x50
        Caps version		1.1
    PCI capability
        Caps class		Message Signalled Interrupts
        Caps offset		0x60
    PCI capability
        Caps class		PCI Express
        Caps offset		0x70
        Device type		Root Complex Integrated Endpoint Device
        Port			0
        Version			1.0
        Link width		0x (max 0x)

    Description			Data Aquisition and Signal Processing Device
    Location			bus 0 (0x00), device 4 (0x04), function 0 (0x00)
    Common header
        Vendor ID		0x8086
        Model ID		0x1603
        Revision ID		0x09
        PI			0x00
        SubClass		0x80
        BaseClass		0x11
        Cache Line		0x00
        Latency			0x00
        Header			0x00
    PCI header
        Address 0 (memory)	0xF1110000
        Subvendor ID		0x17AA
        Subsystem ID		0x222B
        Int. Line		0x10
        Int. Pin		0x01
    PCI capability
        Caps class		Message Signalled Interrupts
        Caps offset		0x90
    PCI capability
        Caps class		Power Management
        Caps offset		0xD0
        Caps version		1.2
    PCI capability
        Caps class		Vendor Dependant
        Caps offset		0xE0

    Description			USB Controller
    Location			bus 0 (0x00), device 20 (0x14), function 0 (0x00)
    Common header
        Vendor ID		0x8086
        Model ID		0x9CB1
        Revision ID		0x03
        PI			0x30
        SubClass		0x03
        BaseClass		0x0C
        Cache Line		0x00
        Latency			0x00
        Header			0x00
    PCI header
        Address 0 (memory)	0xF1100000
        Subvendor ID		0x17AA
        Subsystem ID		0x222B
        Int. Line		0x00
        Int. Pin		0x01
    PCI capability
        Caps class		Power Management
        Caps offset		0x70
        Caps version		1.1
    PCI capability
        Caps class		Message Signalled Interrupts
        Caps offset		0x80

    Description			Communication Device
    Location			bus 0 (0x00), device 22 (0x16), function 0 (0x00)
    Common header
        Vendor ID		0x8086
        Model ID		0x9CBA
        Revision ID		0x03
        PI			0x00
        SubClass		0x80
        BaseClass		0x07
        Cache Line		0x00
        Latency			0x00
        Header			0x80
    PCI header
        Address 0 (memory)	0xF111D000
        Subvendor ID		0x17AA
        Subsystem ID		0x222B
        Int. Line		0x00
        Int. Pin		0x01
    PCI capability
        Caps class		Power Management
        Caps offset		0x50
        Caps version		1.2
    PCI capability
        Caps class		Message Signalled Interrupts
        Caps offset		0x8C

    Description			PCI to PCI Bridge
    Location			bus 0 (0x00), device 28 (0x1C), function 0 (0x00)
    Common header
        Vendor ID		0x8086
        Model ID		0x9C90
        Revision ID		0xE3
        PI			0x00
        SubClass		0x04
        BaseClass		0x06
        Cache Line		0x10
        Latency			0x00
        Header			0x81
    PCI header
        Primary bus		0x00
        Secondary bus		0x02
        Int. Line		0x00
        Int. Pin		0x01
    PCI capability
        Caps class		PCI Express
        Caps offset		0x40
        Device type		Root Port of PCI-E Root Complex
        Port			1
        Version			2.0
        Physical slot		Integrated device
        Link width		0x (max 1x)
    PCI capability
        Caps class		Message Signalled Interrupts
        Caps offset		0x80
    PCI capability
        Caps class		Subsystem Vendor
        Caps offset		0x90
        SubVendor ID		0x17AA
        SubSystem ID		0x222B
    PCI capability
        Caps class		Power Management
        Caps offset		0xA0
        Caps version		1.2

    Description			PCI to PCI Bridge
    Location			bus 0 (0x00), device 28 (0x1C), function 1 (0x01)
    Common header
        Vendor ID		0x8086
        Model ID		0x9C94
        Revision ID		0xE3
        PI			0x00
        SubClass		0x04
        BaseClass		0x06
        Cache Line		0x10
        Latency			0x00
        Header			0x81
    PCI header
        Primary bus		0x00
        Secondary bus		0x06
        Int. Line		0x00
        Int. Pin		0x03
    PCI capability
        Caps class		PCI Express
        Caps offset		0x40
        Device type		Root Port of PCI-E Root Complex
        Port			3
        Version			2.0
        Physical slot		#0
        Presence detect		yes
        Link width		1x (max 1x)
    PCI capability
        Caps class		Message Signalled Interrupts
        Caps offset		0x80
    PCI capability
        Caps class		Subsystem Vendor
        Caps offset		0x90
        SubVendor ID		0x17AA
        SubSystem ID		0x222B
    PCI capability
        Caps class		Power Management
        Caps offset		0xA0
        Caps version		1.2

    Description			PCI to ISA Bridge
    Location			bus 0 (0x00), device 31 (0x1F), function 0 (0x00)
    Common header
        Vendor ID		0x8086
        Model ID		0x9CC7
        Revision ID		0x03
        PI			0x00
        SubClass		0x01
        BaseClass		0x06
        Cache Line		0x00
        Latency			0x00
        Header			0x80
    PCI header
        Subvendor ID		0x17AA
        Subsystem ID		0x222B
        Int. Line		0x00
        Int. Pin		0x00
    PCI capability
        Caps class		Vendor Dependant
        Caps offset		0xE0

    Description			Serial ATA Controller
    Location			bus 0 (0x00), device 31 (0x1F), function 2 (0x02)
    Common header
        Vendor ID		0x8086
        Model ID		0x9C83
        Revision ID		0x03
        PI			0x01
        SubClass		0x06
        BaseClass		0x01
        Cache Line		0x00
        Latency			0x00
        Header			0x00
    PCI header
        Address 0 (port)	0x00003088
        Address 1 (port)	0x0000309C
        Address 2 (port)	0x00003080
        Address 3 (port)	0x00003098
        Address 4 (port)	0x00003060
        Address 5 (memory)	0xF1120000
        Subvendor ID		0x17AA
        Subsystem ID		0x222B
        Int. Line		0x00
        Int. Pin		0x02
    PCI capability
        Caps class		Message Signalled Interrupts
        Caps offset		0x80
    PCI capability
        Caps class		Power Management
        Caps offset		0x70
        Caps version		1.2
    PCI capability
        Caps class		0x12
        Caps offset		0xA8

    Description			SMBus Controller
    Location			bus 0 (0x00), device 31 (0x1F), function 3 (0x03)
    Common header
        Vendor ID		0x8086
        Model ID		0x9CA2
        Revision ID		0x03
        PI			0x00
        SubClass		0x05
        BaseClass		0x0C
        Cache Line		0x00
        Latency			0x00
        Header			0x00
    PCI header
        Address 0 (memory)	0xF111C000
        Address 4 (port)	0x0000EFA0
        Subvendor ID		0x17AA
        Subsystem ID		0x222B
        Int. Line		0x12
        Int. Pin		0x03

    Description			Data Aquisition and Signal Processing Device
    Location			bus 0 (0x00), device 31 (0x1F), function 6 (0x06)
    Common header
        Vendor ID		0x8086
        Model ID		0x9CA4
        Revision ID		0x03
        PI			0x00
        SubClass		0x80
        BaseClass		0x11
        Cache Line		0x00
        Latency			0x00
        Header			0x00
    PCI header
        Address 0 (memory)	0xF111F000
        Subvendor ID		0x17AA
        Subsystem ID		0x222B
        Int. Line		0x12
        Int. Pin		0x03
    PCI capability
        Caps class		Power Management
        Caps offset		0x50
        Caps version		1.2
    PCI capability
        Caps class		Message Signalled Interrupts
        Caps offset		0x80

    Description			Network Controller
    Location			bus 6 (0x06), device 0 (0x00), function 0 (0x00)
    Common header
        Vendor ID		0x8086
        Model ID		0x095A
        Revision ID		0x59
        PI			0x00
        SubClass		0x80
        BaseClass		0x02
        Cache Line		0x10
        Latency			0x00
        Header			0x00
    PCI header
        Address 0 (memory)	0xF1000000
        Subvendor ID		0x8086
        Subsystem ID		0x9010
        Int. Line		0x00
        Int. Pin		0x01
    PCI capability
        Caps class		Power Management
        Caps offset		0xC8
        Caps version		1.2
    PCI capability
        Caps class		Message Signalled Interrupts
        Caps offset		0xD0
    PCI capability
        Caps class		PCI Express
        Caps offset		0x40
        Device type		PCI-E Endpoint Device
        Port			0
        Version			2.0
        Link width		1x (max 1x)
    Extended capabilities
        Caps class		Advanced Error Reporting
        Caps offset		0x100
        Caps class		Device Serial Number
        Caps offset		0x140
        Caps class		0x18
        Caps offset		0x14C
        Caps class		0x1E
        Caps offset		0x154

    DMI
    -------------------------------------------------------------------------
    DMI Processor
        manufacturer		Intel(R) Corporation
        model			Intel(R) Core(TM) M-5Y71 CPU @ 1.20GHz
        clock speed		1200.0 MHz
        FSB speed		100.0 MHz
        multiplier		12.0x

    DMI Physical Memory Array
        location		Motherboard
        usage			System Memory
        correction		None
        max capacity		16384 MBytes
        max# of devices		2

    DMI Memory Device
        designation		ChannelA
        format			Chip
        type			unknown
        total width		64 bits
        data width		64 bits
        size			4096 MBytes

    DMI Memory Device
        designation		ChannelB
        format			Chip
        type			unknown
        total width		64 bits
        data width		64 bits
        size			4096 MBytes

    DMI System Information
        manufacturer		LENOVO
        product			20CGCTO1WW
        version			ThinkPad Helix 2nd
        serial			R90F7WAP
        SKU			LENOVO_MT_20CG_BU_Think_FM_ThinkPad Helix 2nd
        family			ThinkPad Helix 2nd

    DMI Baseboard
        vendor			LENOVO
        model			20CGCTO1WW
        revision		SDK0E50512 STD
        serial			W1KS52311AM

    DMI System Enclosure
        manufacturer		LENOVO
        chassis type		HandHeld
        chassis serial		R90F7WAP

    DMI Port Connector
        designation		Not Available (internal)
        designation		USB 1 (external)
        port type		USB
        connector		Access Bus (USB)

    DMI Port Connector
        designation		Not Available (internal)
        designation		USB 2 (external)
        port type		USB
        connector		Access Bus (USB)

    DMI Port Connector
        designation		Not Available (internal)
        designation		USB 3 (external)
        port type		USB
        connector		Access Bus (USB)

    DMI Port Connector
        designation		Not Available (internal)
        designation		USB 4 (external)
        port type		USB
        connector		Access Bus (USB)

    DMI Port Connector
        designation		Not Available (internal)
        designation		USB 5 (external)
        port type		USB
        connector		Access Bus (USB)

    DMI Port Connector
        designation		Not Available (internal)
        designation		USB 6 (external)
        port type		USB
        connector		Access Bus (USB)

    DMI Port Connector
        designation		Not Available (internal)
        designation		USB 7 (external)
        port type		USB
        connector		Access Bus (USB)

    DMI Port Connector
        designation		Not Available (internal)
        designation		USB 8 (external)
        port type		USB
        connector		Access Bus (USB)

    DMI Port Connector
        designation		Not Available (internal)
        designation		Ethernet (external)
        port type		Network Port
        connector		RJ-45

    DMI Port Connector
        designation		Not Available (internal)
        designation		External Monitor (external)
        port type		Video Port
        connector		DB-15 female

    DMI Port Connector
        designation		Not Available (internal)
        designation		Mini DisplayPort (external)
        port type		Video Port

    DMI Port Connector
        designation		Not Available (internal)
        designation		DisplayPort/DVI-D (external)
        port type		Video Port

    DMI Port Connector
        designation		Not Available (internal)
        designation		DisplayPort/HDMI (external)
        port type		Video Port

    DMI Port Connector
        designation		Not Available (internal)
        designation		Headphone/Microphone Combo Jack1 (external)
        port type		Audio Port
        connector		Mini Jack (headphones)

    DMI Port Connector
        designation		Not Available (internal)
        designation		Headphone/Microphone Combo Jack2 (external)
        port type		Audio Port
        connector		Mini Jack (headphones)

    DMI Extension Slot
        designation		Media Card Slot
        type			1
        populated		no

    DMI Extension Slot
        designation		SimCard Slot
        type			1
        populated		no

    DMI BIOS
        vendor			LENOVO
        version			N17ET70W (1.70 )
        date			12/26/2014
        ROM size		16384 KB

    Storage
    -------------------------------------------------------------------------
    Drive	0
        Device Path		\\?\scsi#disk&ven_samsung&prod_mznte128hmgr-000#4&20ae874c&0&030000
        Type			Fixed
        Name			SAMSUNG MZNTE128HMGR-000L1
        Capacity		119.2 GB
        SMART Support		Yes

    Graphics
    -------------------------------------------------------------------------
    Number of adapters		1

    Graphic APIs
    -------------------------------------------------------------------------
    API				Intel I/O

    Display Adapters
    -------------------------------------------------------------------------
    Display adapter 0
        Display name		\\.\DISPLAY1
        Name			Intel(R) HD Graphics 5300
        Board Manufacturer	Lenovo
        Memory size		1024 MB
        PCI device		bus 0 (0x0), device 2 (0x2), function 0 (0x0)
        Vendor ID		0x8086 (0x17AA)
        Model ID		0x161E (0x222B)
        Performance Level	0

    Win32_VideoController		AdapterRAM = 0x40000000 (1073741824)
    Win32_VideoController		DriverVersion = 10.18.10.3977
    Win32_VideoController		DriverDate = 10/09/2014

    Monitor 0
        Model			 ()
        ID			LEN40D3
        Serial
        Manufacturing Date	Week 0, Year 2014
        Size			11.6 inches
        Max Resolution		1920 x 1080 @ 59 Hz
        Horizontal Freq. Range	0-0 kHz
        Vertical Freq. Range	0-0 Hz
        Max Pixel Clock		0 MHz
        Gamma Factor		2.2

    Software
    -------------------------------------------------------------------------
    Windows Version			Microsoft Windows 8.1 (6.3) 64-bit   (Build 9600)
    DirectX Version			11.0

