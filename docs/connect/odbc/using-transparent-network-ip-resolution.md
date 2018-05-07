---
title: 透過ネットワーク IP 解決を使用して |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d255208f-d486-4ad3-8080-61c6e0261825
caps.latest.revision: 2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2d76e50b4761e8d1a32bbcfc4606778f96513ed1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-transparent-network-ip-resolution"></a>透過ネットワーク IP 解決を使用してください。
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

TransparentNetworkIPResolution がホスト名の最初の解決済みの IP しない場合、ドライバーの接続シーケンスに影響する、SQL Server 用 Microsoft ODBC Driver 13.1 で利用できる既存 MultiSubnetFailover 機能のリビジョン応答し、ホスト名に関連付けられている複数の ip アドレスがあります。 次の 3 つの接続シーケンスを提供する MultiSubnetFailover とやり取りします。

* 0: 並列ですべての Ip に続く IP が試行されると、1 つ
* 1: すべての ip アドレスは、並列で試行
* 2: すべての Ip が試行された 1 つずつ

|TransparentNetworkIPResolution|MultiSubnetFailover|動作|
|:-:|:-:|:-:|
|(既定値)。|(既定値)。|0|
|(既定値)。|有効|1|
|(既定値)。|Disabled|0|
|有効|(既定値)。|0|
|有効|有効|1|
|有効|Disabled|0|
|Disabled|(既定値)。|2|
|Disabled|有効|1|
|Disabled|Disabled|2|

`TransparentNetworkIPResolution` DSN と接続文字列キーワードは、この設定は、接続文字列のレベルを制御します。 既定値は有効です。

Keyword|値|既定値
-|-|-
`TransparentNetworkIPResolution`|`Yes`, `No`|`Yes`

`SQL_COPT_SS_TNIR`前の接続属性では、アプリケーションがプログラムによって、この設定を制御します。

接続属性|   サイズ/型|  既定値| 値| Description
-|-|-|-|-
`SQL_COPT_SS_TNIR` (1249)| `SQL_IS_INTEGER`または`SQL_IS_UINTEGER`| `SQL_IS_ON`(1), `SQL_IS_OFF`(0)|`SQL_IS_ON`|有効または TNIR を無効にします。

<a name="for-more-information-about-multisubnetfailover-see-odbc-driver-on-linux-and-macos---high-availability-and-disaster-recoveryconnectodbclinux-macodbc-driver-on-linux-support-for-high-availability-disaster-recoverymd"></a>MultiSubnetFailover の詳細については、次を参照してください[ODBC Driver on Linux and macOS - 高可用性と災害復旧。](../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md)
--------------------------------------------------
## <a name="see-also"></a>参照  
* [Microsoft ODBC Driver for SQL Server on Windows](../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)
* [SQL Server マルチ サブネット クラスタ リング (SQL Server)](https://msdn.microsoft.com/library/ff878716.aspx#RelatedContent)
