---
title: 透過ネットワーク IP 解決を使用して |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d255208f-d486-4ad3-8080-61c6e0261825
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 94c7f34ebf66f4bf33acf51e44397a74de2367e0
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801722"
---
# <a name="using-transparent-network-ip-resolution"></a>透過的なネットワーク IP の解決の使用
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

TransparentNetworkIPResolution はホスト名の最初の解決された IP しない場合、ドライバーの接続シーケンスに影響を与える、SQL Server 用 Microsoft ODBC Driver 13.1 で利用できる既存 MultiSubnetFailover 機能のリビジョン応答し、ホスト名に関連付けられている複数の ip アドレスがあります。 MultiSubnetFailover は、次の 3 つの接続シーケンスを提供するとやり取りします。

* 0: IP が試みられると、1 つ後に並列ですべての ip アドレス
* 1: すべての ip アドレスは、並列で試行します。
* 2: すべての ip アドレスが試行された 1 つずつ

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

`TransparentNetworkIPResolution` DSN と接続文字列キーワードが接続文字列のレベルでは、この設定を制御します。 既定値が有効になっているとします。

Keyword|値|既定
-|-|-
`TransparentNetworkIPResolution`|`Yes`, `No`|`Yes`

`SQL_COPT_SS_TNIR`接続前の属性により、アプリケーションがプログラムでこの設定を制御します。

接続属性|   サイズ/型|  既定| [値]| [説明]
-|-|-|-|-
`SQL_COPT_SS_TNIR` (1249)| `SQL_IS_INTEGER` または `SQL_IS_UINTEGER`| `SQL_IS_ON`(1)、`SQL_IS_OFF`(0)|`SQL_IS_ON`|有効または TNIR を無効にします。

<a name="for-more-information-about-multisubnetfailover-see-odbc-driver-on-linux-and-macos---high-availability-and-disaster-recoveryconnectodbclinux-macodbc-driver-on-linux-support-for-high-availability-disaster-recoverymd"></a>MultiSubnetFailover の詳細については、次を参照してください[ODBC Driver on Linux と macOS の高可用性とディザスター リカバリー。](../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md)
--------------------------------------------------
## <a name="see-also"></a>参照  
* [Microsoft ODBC Driver for SQL Server on Windows](../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)
* [SQL Server マルチサブネット クラスタリング (SQL Server)](https://msdn.microsoft.com/library/ff878716.aspx#RelatedContent)
