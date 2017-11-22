---
title: "Analytics Platform System: スケール アウト データ ウェアハウスの新機能"
author: happynicolle
ms.author: nicw;barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.suite: sql
ms.custom: 
ms.technology: mpp-data-warehouse
description: "Microsoft® Analytics Platform System、MPP SQL Server 並列データ ウェアハウスをホストするスケール アウト、内部設置型アプライアンスの新機能を参照してください。"
ms.date: 11/28/2016
ms.topic: article
ms.openlocfilehash: 3dc1a338ced5aa90ada112b97c4a6f13777da409
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="whats-new-in-analytics-platform-system-2016-a-scale-out-mpp-data-warehouse"></a>Analytics Platform System 2016、スケール アウト MPP データ ウェアハウスの新機能
Microsoft® Analytics Platform System (APS) 2016、アプライアンスの最新の更新プログラムは、スケール アウト、内部設置型のアプライアンス MPP SQL Server 並列データ ウェアハウスをホストする新しい内容を確認します。 

## <a name="sql-server-2016"></a>SQL Server 2016

APS 2016 では、最新の SQL Server 2016 リリースで実行し、既定のデータベース互換性レベル 130 を使用します。  SQL Server 2016 では、PolyBase のクラスター化列ストア インデックスと Kerberos のセカンダリ インデックスなどの新機能の一部をサポートすることです。 


## <a name="t-sql"></a>T-SQL
APS 2016 では、それらの改良の T-SQL の互換性をサポートします。  これらの追加の言語要素容易にできるように SQL Server およびその他のデータ ソースからの移行します。 

- [列レベルの SQL 照合順序][]に加えて Windows 照合順序がサポートされています。
- [クラスター化列ストア インデックスの非クラスター化インデックス][]クラスター化列ストア インデックスに特定の値を検索するクエリのパフォーマンスが向上します。 
- [このオプションを選択するとしてください.に][] 
- [sp_spaceused()][]ディスク領域が使用されるか、テーブルまたはデータベースで予約されていますが表示されます。
- [幅の広いテーブル][]サポートは SQL Server 2016 と同じです。 行サイズの 32 K の以前の制限は存在しません。 

### <a name="data-types"></a>データ型

- [Varchar (max)][]、 [nvarchar (max)][]と[varbinary (max)][]です。 これらの LOB データ型では、2 GB の最大サイズがあります。 オブジェクトによって使用されるこれらの読み込みに[bcp ユーティリティ][]です。 Polybase と dwloader は、これらのデータ型を現在サポートされません。 
- [SYSNAME][]
- [一意識別子][]
- [数値][]および DECIMAL データ型。

### <a name="window-functions"></a>ウィンドウ関数

- [ROWS または RANGE][] SELECT ステートメントの OVER 句でします。
- [FIRST_VALUE][]
- [LAST_VALUE][]
- [CUME_DIST][]
- [PERCENT_RANK][]

### <a name="security-functions"></a>セキュリティ関数

- [CHECKSUM()][]と[BINARY_CHECKSUM()][]
- [HAS_PERMS_BY_NAME()][]

### <a name="additional-functions"></a>追加の関数

- [NEWID()][]
- [RAND()][]

## <a name="polybasehadoop-enhancements"></a>PolyBase/Hadoop の機能強化

- Hortonworks HDP 2.4 と HDP 2.5 との互換性
- データベース スコープ資格情報を使用して Kerberos をサポートします。
- Azure ストレージ Blob の資格情報のサポート

## <a name="install-and-upgrade-enhancements"></a>インストールとアップグレードの機能強化

### <a name="enterprise-architecture-updates"></a>エンタープライズ アーキテクチャの更新プログラム
最新のファームウェアとドライバーの更新は、セキュリティの修正が含まれてをインストール、既存のアプライアンスを APS 2016 にアップグレードします。 

HPE または DELL から新しいアプライアンスに、最新の更新プログラムが含まれていますとします。

- 最新世代プロセッサのサポート (Broadwell)
- DDR4 Dimm への更新
- DIMM スループットの向上

### <a name="integration"></a>統合

- 完全修飾ドメイン名 (FQDN) をサポートできるようになりますアプライアンスにドメインの信頼関係をセットアップします。 
- FQDN を使用するのには、完全なアップグレードを行うと、アップグレード中にオプトインする必要があります。 

### <a name="reduced-downtime"></a>ダウンタイムの短縮
APS 2016 へのアップグレードをインストールまたは方で、以前のリリースよりも少ないダウンタイムが必要です。 ダウンタイムをインストールまたはアップグレードを減らします。 

 - 2016 年 6 月経由のすべての更新プログラムを含むイメージを使用して WSUS 更新プログラムを適用する効率化
 - ドライバーおよびファームウェアの更新とセキュリティ更新プログラムを適用します。
 - ダウンロードする必要はありませんでをインストールする準備ができるように、アプライアンス上で最新の修正プログラムとアプライアンス検証ユーティリティ (PAV) を配置します。


<!--MSDN references-->
[database compatibility level 130]:https://msdn.microsoft.com/library/bb510680.aspx
[列レベルの SQL 照合順序]:https://msdn.microsoft.com/library/ms143726.aspx
[クラスター化列ストア インデックスの非クラスター化インデックス]:https://msdn.microsoft.com/library/ms188783.aspx
[Varchar (max)]:https://msdn.microsoft.com/library/ms176089.aspx
[nvarchar (max)]:https://msdn.microsoft.com/library/ms186939.aspx
[varbinary (max)]:https://msdn.microsoft.com/library/ms188362.aspx
[SYSNAME]:https://msdn.microsoft.com/library/ms188021.aspx
[このオプションを選択するとしてください.に]:https://msdn.microsoft.com/library/ms188029.aspx
[sp_spaceused()]:https://msdn.microsoft.com/library/ms188776.aspx
[幅の広いテーブル]:https://msdn.microsoft.com/library/ms143432.aspx
[BULK INSERT]:https://msdn.microsoft.com/library/ms188365.aspx
[bcp ユーティリティ]:https://msdn.microsoft.com/library/ms162802.aspx
[一意識別子]:https://msdn.microsoft.com/library/ms187942.aspx
[数値]:https://msdn.microsoft.com/library/ms187746.aspx
[ROWS または RANGE]:https://msdn.microsoft.com/library/ms189461.aspx
[FIRST_VALUE]:https://msdn.microsoft.com/library/hh213018.aspx
[LAST_VALUE]:https://msdn.microsoft.com/library/hh231517.aspx
[CUME_DIST]:https://msdn.microsoft.com//library/hh231078.aspx
[PERCENT_RANK]:https://msdn.microsoft.com/library/hh213573.aspx
[CHECKSUM()]:https://msdn.microsoft.com/library/ms189788.aspx
[BINARY_CHECKSUM()]:https://msdn.microsoft.com/library/ms173784.aspx
[HAS_PERMS_BY_NAME()]:https://msdn.microsoft.com/library/ms189802.aspx
[NEWID()]:https://msdn.microsoft.com/library/ms190348.aspx
[RAND()]:https://msdn.microsoft.com/library/ms177610.aspx


  

  


