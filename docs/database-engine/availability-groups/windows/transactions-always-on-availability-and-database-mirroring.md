---
title: トランザクション - Always On 可用性グループとデータベース ミラーリング | Microsoft Docs
ms.custom: ''
ms.date: 11/01/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- cross-database transactions [SQL Server]
- transactions [database mirroring]
- Availability Groups [SQL Server], interoperability
- troubleshooting [SQL Server], cross-database transactions
ms.assetid: 9f7ed895-ad65-43e3-ba08-00d7bff1456d
caps.latest.revision: 33
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 77e578babc3efa230a0da00c42187e50e650dd32
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="transactions---availability-groups-and-database-mirroring"></a>トランザクション - 可用性グループとデータベース ミラーリング
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

このトピックでは、Always On 可用性グループとデータベース ミラーリングでの複数データベースにまたがるトランザクションと分散トランザクションのサポートについて説明します。  

## <a name="support-for-distributed-transactions"></a>分散トランザクションのサポート

SQL Server 2017 では、可用性グループのデータベースに対して分散トランザクションがサポートされています。 このサポートには、SQL Server の同じインスタンス上のデータベース、または SQL Server の異なるインスタンス上のデータベースが含まれています。 分散トランザクションは、データベース ミラーリング用に構成されたデータベースではサポートされていません。

>[!NOTE]
>[!INCLUDE[SQL Server 2016]](../../../includes/sssql15-md.md)]SQL Server 2016 では、可用性グループのデータベースに対して分散トランザクションが制限付きでサポートされます。 可用性グループのデータベースを使用した分散トランザクションは、そのトランザクションの他のインスタンスが、SQL Server の同じインスタンスにない場合に限りサポートされていました。 詳細については、「[SQL Server 2016 DTC Support In Availability Groups](http://blogs.technet.microsoft.com/dataplatform/2016/01/25/sql-server-2016-dtc-support-in-availability-gr)」 (可用性グループでの SQL Server 2016 DTC のサポート) を参照してください。

分散トランザクション対応の可用性グループの構成については、「[Configure Availability Group for Distributed Transactions](configure-availability-group-for-distributed-transactions.md)」 (分散トランザクション対応の可用性グループを構成する)」を参照してください。

詳細については、次を参照してください。

- [DTC 管理ガイド](http://msdn.microsoft.com/library/ms681291.aspx)
- [DTC 開発者ガイド](http://msdn.microsoft.com/library/ms679938.aspx)
- [DTC プログラマ リファレンス](http://msdn.microsoft.com/library/ms686108.aspx)

## <a name="sql-server-2016-and-before-support-for-cross-database-transactions-within-the-same-sql-server-instance"></a>SQL Server 2016 以前: 同じ SQL Server インスタンス内での複数データベースにまたがるトランザクションのサポート  

SQL Server 2016 以前では、可用性グループに対して、同じ SQL Server インスタンス内での複数データベースにまたがるトランザクションはサポートされていません。 つまり、同じ SQL Server インスタンスでの複数データベースにまたがるトランザクションにおいて 2 つのデータベースをホストすることができない可能性があります。 これは、これらのデータベースが同じ可用性グループの一部である場合でも当てはまります。  
  
複数のデータベースにまたがるトランザクションは、データベース ミラーリングでもサポートされていません。  
  
##  <a name="dtcsupport"></a> SQL Server 2016: 分散トランザクションのサポート  
分散トランザクションは、可用性グループでサポートされています。 これは、2 つの異なる SQL Server インスタンスでホストされるデータベース間の分散トランザクションに当てはまります。 また、SQL Server と DTC に準拠した別のサーバー間の分散トランザクションにも当てはまります。  
 
Microsoft 分散トランザクション コーディネーター (MSDTC または DTC) は、分散システムのトランザクション インフラストラクチャを提供する Windows サービスです。 MSDTC では、クライアント アプリケーションに対して、1 つのトランザクションに複数のデータ ソースを含め、その後、トランザクションに含まれるすべてのサーバーにコミットすることを許可します。 たとえば、MSDTC を使用して、さまざまなサーバーの複数のデータベースにわたるトランザクションを調整することができます。

SQL Server 2016 では、トランザクションの 1 つ以上のデータベースが可用性グループに含まれる場合、分散トランザクションを使用する機能を導入します。 SQL Server 2016 より前の分散トランザクションでは、可用性グループのデータベースはサポートされていませんでした。 SQL Server 2016 では、データベースごとにリソース マネージャーを登録できます。 この新機能を使用すると、分散トランザクションでデータベースを可用性グループに含めることができます。
  
 次の要件が満たされる必要があります。  
  
-   可用性グループは、Windows Server 2016 または Windows Server 2012 R2 上で実行されている必要があります。 Windows Server 2012 R2 の場合は、[https://support.microsoft.com/en-us/kb/3090973](https://support.microsoft.com/en-us/kb/3090973) で入手できる KB3090973 の更新プログラムをインストールする必要があります。  
  
-   可用性グループは、**CREATE AVAILABILITY GROUP** コマンドと **WITH DTC\_SUPPORT = PER_DB** 句を使って作成する必要があります。 現在、既存の可用性グループを変更することはできません。  

- 可用性グループに参加するすべての SQL Server インスタンスは、SQL Server 2016 以降である必要があります。
 
 ## <a name="non-support-for-distributed-transactions"></a>分散トランザクションの非サポート
 次の場合、分散トランザクションはサポートされません。
 
 - SQL Server 2016 以前で、トランザクションに関係する複数のデータベースが同じ可用性グループに含まれる場合。
 
 - SQL Server 2016 以前で、少なくとも 1 つのデータベースが可用性グループにあり、別のデータベースが同じインスタンスの SQL Server にある場合。 
 
 - 分散トランザクションを有効にして可用性グループが作成されなかった場合。
 
 - データベース ミラーリング
 
 > [!IMPORTANT]
 > ご利用の環境で DTC が解決できないトランザクションの適切な既定の結果を判断します。  既定の結果の構成方法については、「 [in-doubt xact resolution サーバー構成オプション](../../../database-engine/configure-windows/in-doubt-xact-resolution-server-configuration-option.md)」を参照してください。
  
## <a name="example-scenario-with-database-mirroring"></a>データベース ミラーリングのサンプル シナリオ  
 次に示すデータベース ミラーリングの例では、論理的な不一致が発生するしくみについて説明します。 この例では、アプリケーションは複数データベースにまたがるトランザクションを使用して 2 行のデータを挿入します。一方の行は、ミラー化されたデータベース A 内のテーブルに挿入され、もう一方の行は、別のデータベース B 内のテーブルに挿入されます。データベース A は、自動フェールオーバーを伴う高い安全性モードでミラー化されています。 トランザクションがコミットされている間、データベース A は使用できなくなり、ミラーリング セッションはデータベース A のミラーに自動的にフェールオーバーされます。  
  
 フェールオーバー後、複数データベースにまたがるトランザクションは、データベース B では正常にコミットされますが、フェールオーバーされたデータベースではコミットされない場合があります。 これは、障害発生前に、複数データベースにまたがるトランザクションのログがデータベース A の元のプリンシパル サーバーからミラー サーバーに送信されなかった場合に発生します。 フェールオーバー後、そのトランザクションは新しいプリンシパル サーバーに存在しなくなります。 データベース B に挿入されたデータはそのまま保たれますが、データベース A に挿入されたデータは失われているため、データベース A と B は一致しなくなります。  
  
 同様の状況は、MS DTC トランザクションを使用する際に発生する場合があります。 たとえば、フェールオーバー後、新しいプリンシパルが MS DTC にアクセスします。 ただし、MS DTC は、新しいプリンシパル サーバーを認識せず、"コミットの準備が整った" トランザクションを終了します。これらのトランザクションは、他のデータベースでコミットされていると見なされます。  
  
> [!NOTE]  
>  このトピックで承認されていない DTC とデータベース ミラーリングの使用または DTC と可用性グループの使用はサポートされていません。  これは、DTC に関係しない部分はサポートされないことを意味するものではありません。ただし、分散トランザクションの不適切な使用により発生する問題はサポートされません。  
  
## <a name="next-steps"></a>次の手順  
 [Always On availability groups: Interoperability &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-availability-groups-interoperability-sql-server.md)  
  
  
