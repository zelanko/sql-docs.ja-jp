---
title: "SQL Server のレプリケーション | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "レプリケーション [SQL Server], 概要"
  - "レプリケーション [SQL Server]"
ms.assetid: 3a5f4592-3c61-4b4d-9ceb-39716aeeba41
caps.latest.revision: 58
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 58
---
# SQL Server のレプリケーション
  レプリケーションとは、あるデータベースから別のデータベースにデータやデータベース オブジェクトをコピーおよび配布し、それらのデータベースを同期させて一貫性を保つための一連のテクノロジです。 レプリケーションを使用すると、ローカル エリア ネットワーク、ワイド エリア ネットワーク、ダイヤルアップ接続、ワイヤレス接続、インターネットなどを経由して、別の場所や、リモート ユーザーまたはモバイル ユーザーにデータを配布することができます。  
  
 トランザクション レプリケーションは、高いスループットが必要とされるサーバー間のシナリオで使用されるのが一般的です。たとえば、スケーラビリティと可用性の向上、データ ウェアハウジングとレポート、複数サイトからのデータの統合、異種データの統合、バッチ処理のオフロードなどのシナリオで使用されます。 マージ レプリケーションは、データの競合の可能性があるモバイル アプリケーションや分散サーバー アプリケーションを主な対象としています。 モバイル ユーザーとのデータ交換、店舗販売時点管理 (POS) アプリケーション、複数サイトからのデータの統合などのシナリオが一般的です。 スナップショット レプリケーションは、トランザクション レプリケーションとマージ レプリケーションに初期データセットを提供するために使用されます。データの完全な更新が必要な場合にも使用できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、この 3 種類のレプリケーションにより、企業全体のデータの同期のための強力かつ柔軟なシステムが提供されます。 SQLCE 3.5 および SQLCE 4.0 に対するレプリケーションは [!INCLUDE[win8srv](../../includes/win8srv-md.md)] と [!INCLUDE[win8](../../includes/win8-md.md)] の両方でサポートされます。  
  
 レプリケーションの代替手段として、Microsoft Sync Framework を使用してデータベースを同期できます。 Sync Framework には、SQL Server、SQL Server Express、SQL Server Compact、および SQL Azure の各データベース間での同期を容易にするコンポーネントと、直感的かつ柔軟性の高い API が含まれています。 また、Sync Framework には、SQL Server データベースと、ADO.NET と互換性があるその他のデータベースとの間で同期を行うために使用できるクラスもあります。 Sync Framework データベース同期コンポーネントの詳細なドキュメントについては、次を参照してください。 [データベースの同期](http://go.microsoft.com/fwlink/?LinkId=209079)します。 Sync Framework の概要については、次を参照してください。 [Microsoft Sync Framework デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=209078)します。 Sync Framework とマージ レプリケーションとの間で比較では、次を参照してください [を同期するデータベースの概要。](http://msdn.microsoft.com/library/bb902818\(SQL.110\).aspx)  
  
 **領域ごとのコンテンツの参照**  
 ![小さいファイル フォルダー アイコン](../../analysis-services/media/filefolder-small.png "小さいファイル フォルダー アイコン") [新機能](../../relational-databases/replication/what-s-new-replication.md)  
  
 ![小さいファイル フォルダー アイコン](../../analysis-services/media/filefolder-small.png "小さいファイル フォルダー アイコン") [旧バージョンとの互換性](../../relational-databases/replication/replication-backward-compatibility.md)  
  
 ![小さいファイル フォルダー アイコン](../../analysis-services/media/filefolder-small.png "小さいファイル フォルダー アイコン") [レプリケーション機能とタスク](../../relational-databases/replication/replication-features-and-tasks.md)  
  
 ![小さいファイル フォルダー アイコン](../../analysis-services/media/filefolder-small.png "小さいファイル フォルダー アイコン") [テクニカル リファレンス](../../relational-databases/replication/technical-reference-replication.md)  
  
  