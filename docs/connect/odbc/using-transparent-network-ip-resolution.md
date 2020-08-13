---
title: 透過的なネットワーク IP の解決の使用
description: ODBC Driver for SQL Server での透過的なネットワーク IP の解決についてと、MultiSubnetFailover 機能に与える影響について学習します。
ms.custom: ''
ms.date: 05/06/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d255208f-d486-4ad3-8080-61c6e0261825
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 12a8a151902bd4f191fbc79f165f936e991a0226
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87245001"
---
# <a name="using-transparent-network-ip-resolution-with-the-odbc-driver"></a>ODBC ドライバーでの透過的なネットワーク IP の解決の使用
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

TransparentNetworkIPResolution は、ホスト名の最初に解決された IP が応答せず、そのホスト名に関連付けられている IP が複数ある場合に、ドライバーの接続シーケンスに影響する、既存の MultiSubnetFailover 機能が改訂されたものであり、Microsoft ODBC Driver 13.1 for SQL Server で使用できます。 MultiSubnetFailover と連動して、次の 3 つの接続シーケンスを提供します。

* 0:1 つの IP が試行され、その後にすべての IP が並列で試行されます
* 1:すべての IP が並列で試行されます
* 2:すべての IP が 1 つずつ試行されます

|TransparentNetworkIPResolution|MultiSubnetFailover|動作|
|:-:|:-:|:-:|
|(既定値)。|(既定値)。|0|
|(既定値)。|Enabled|1|
|(既定値)。|無効|0|
|Enabled|(既定値)。|0|
|Enabled|Enabled|1|
|Enabled|無効|0|
|無効|(既定値)。|2|
|無効|Enabled|1|
|無効|無効|2|

`TransparentNetworkIPResolution` 接続文字列と DSN キーワードでは、この設定を接続文字列レベルで制御します。 既定値は有効です。

Keyword|値|Default
-|-|-
`TransparentNetworkIPResolution`|`Yes`, `No`|`Yes`

`SQL_COPT_SS_TNIR` の接続前属性を使用すると、アプリケーションでこの設定をプログラムによって制御できます。

接続属性|   サイズ/型|  Default| 値| 説明
-|-|-|-|-
`SQL_COPT_SS_TNIR` (1249)| `SQL_IS_INTEGER` または `SQL_IS_UINTEGER`| `SQL_IS_ON`(1)、`SQL_IS_OFF`(0)|`SQL_IS_ON`|TNIR を有効または無効にします。

<a name="for-more-information-about-multisubnetfailover-see-odbc-driver-on-linux-and-macos---high-availability-and-disaster-recovery"></a>MultiSubnetFailover について詳しくは、「[Linux と macOS の ODBC ドライバー - 高可用性とディザスター リカバリー](linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md)」をご覧ください
--------------------------------------------------
## <a name="see-also"></a>参照  
* [Microsoft ODBC Driver for SQL Server on Windows](windows/microsoft-odbc-driver-for-sql-server-on-windows.md)
* [SQL Server マルチサブネット クラスタリング (SQL Server)](../../sql-server/failover-clusters/windows/sql-server-multi-subnet-clustering-sql-server.md)
