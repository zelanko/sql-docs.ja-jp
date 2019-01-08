---
title: SQL Server のレプリケーション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], about
- replication [SQL Server]
ms.assetid: 3a5f4592-3c61-4b4d-9ceb-39716aeeba41
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 01027aaa813cb3859dfd6d8459b7138a071c0f2d
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/13/2018
ms.locfileid: "53352972"
---
# <a name="sql-server-replication"></a>SQL Server のレプリケーション
  レプリケーションとは、あるデータベースから別のデータベースにデータやデータベース オブジェクトをコピーおよび配布し、それらのデータベースを同期させて一貫性を保つための一連のテクノロジです。 レプリケーションを使用すると、ローカル エリア ネットワーク、ワイド エリア ネットワーク、ダイヤルアップ接続、ワイヤレス接続、インターネットなどを経由して、別の場所や、リモート ユーザーまたはモバイル ユーザーにデータを配布することができます。  
  
 トランザクション レプリケーションは、高いスループットが必要とされるサーバー間のシナリオで使用されるのが一般的です。たとえば、スケーラビリティと可用性の向上、データ ウェアハウジングとレポート、複数サイトからのデータの統合、異種データの統合、バッチ処理のオフロードなどのシナリオで使用されます。 マージ レプリケーションは、データの競合の可能性があるモバイル アプリケーションや分散サーバー アプリケーションを主な対象としています。 モバイル ユーザーとのデータ交換、店舗販売時点管理 (POS) アプリケーション、複数サイトからのデータの統合などのシナリオが一般的です。 スナップショット レプリケーションは、トランザクション レプリケーションとマージ レプリケーションに初期データセットを提供するために使用されます。データの完全な更新が必要な場合にも使用できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、この 3 種類のレプリケーションにより、企業全体のデータの同期のための強力かつ柔軟なシステムが提供されます。 SQLCE 3.5 および SQLCE 4.0 に対するレプリケーションは [!INCLUDE[win8srv](../../includes/win8srv-md.md)] と [!INCLUDE[win8](../../includes/win8-md.md)]の両方でサポートされます。  
  
 レプリケーションの代替手段として、Microsoft Sync Framework を使用してデータベースを同期できます。 Sync Framework には、SQL Server、SQL Server Express、SQL Server Compact、および SQL Azure の各データベース間での同期を容易にするコンポーネントと、直感的かつ柔軟性の高い API が含まれています。 また、Sync Framework には、SQL Server データベースと、ADO.NET と互換性があるその他のデータベースとの間で同期を行うために使用できるクラスもあります。 Sync Framework のデータベース同期コンポーネントの詳細については、「 [データベースの同期](https://go.microsoft.com/fwlink/?LinkId=209079)」を参照してください。 Sync Framework の概要の詳細については、「 [Microsoft Sync Framework デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=209078)」を参照してください。 Sync Framework とマージ レプリケーションとの比較の詳細については、データベースの同期の「 [概要とシナリオ](https://msdn.microsoft.com/library/bb902818\(SQL.110\).aspx)」を参照してください。  
  
 **領域ごとのコンテンツの参照**  
 ![小さいファイル フォルダー アイコン](../../integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")[はの新機能](what-s-new-replication.md)  
  
 ![小さいファイル フォルダー アイコン](../../integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")[旧バージョンとの互換性](replication-backward-compatibility.md)  
  
 ![小さいファイル フォルダー アイコン](../../integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")[レプリケーション機能とタスク](replication-features-and-tasks.md)  
  
 ![小さいファイル フォルダー アイコン](../../integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")[テクニカル リファレンス](technical-reference-replication.md)  
  
  
