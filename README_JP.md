# APISハードウェア情報

## Introduction

APISハードウェア情報は、Sony CSL が開発した自律分散制御の電力相互融通ソフトウェア [APIS](https://github.com/SonyCSL/APIS) により、実際の蓄電システムや DC/DC converter などのハードウェアを用いた電力相互融通システムにおいて、PP2P型の電力融通を実行させるために必要なハードウェア要求に関わる参考情報である。

<br>

<div align="center">
<img src="media/thumbnail.PNG" alt="システム構成" width="600" height="400">
</div>
<br>

本要求は、ユーザーが APIS による電力相互融通を、エミュレーションではなく、実際の蓄電システム間の電力融通を実施する際のハードウェア設計において有用な参考情報であり、ハードウェア動作を保証するものではない。従って、実際に電力相互融通システムに使用するハードウェアに関しては、本情報を参考にしながらユーザー自身が適切に設計・選定・評価・使用すること。

<br>

**電力相互融通システムのハードウェア設計にあたっては、[Document](https://github.com/SonyCSL/apis-hw-info/blob/main/MAIN-DOCUMENT_JP.md) の他に、以下の点に注意すること**


* **APIS のハードウェア制御ポリシー：APIS の制御対象は融通グリッドのみ**
  * DC/DC converter のDCグリッド側の動作モード・電圧(&Droop率)・電流を制御する
  * 蓄電システムの電圧や電流は能動的には制御しない(ステータスを取得するのみ)
    * DC/DC converter のDCグリッド側を制御することによって、(結果的に)蓄電システムに充放電が行われる

<br>

* **APIS のハードウェア保護ポリシー：APIS にはハードウェアの安全保護機能は無い**
  * APIS は、ハードウェア保護が作動しない正常系の範囲内にて、融通制御を実施する
    * 正常系の範囲で動作するよう、apis-main において各設定値(hwConfig.jsonやPolicy.jsonなど)を設定する
    * 異常系においては、APIS がどのような制御を実施しても、ハードウェア自身が(蓄電システム、DC/DC converter 、DCグリッドを含む)ハードウェア側の故障や事故を防ぐよう安全保護を実施する事を想定している



## Documentation
&emsp;[Documentation(JP)](https://github.com/SonyCSL/apis-hw-info/blob/main/MAIN-DOCUMENT_JP.md)
