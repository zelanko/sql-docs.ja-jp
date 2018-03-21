---
title: "データベース エンジンの開発者向けのドキュメント | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: relational-databases-misc
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- developer's guide [SQL Server Database Engine]
- Database Engine [SQL Server], development
ms.assetid: 7638f46c-9e66-48e6-9a9b-425e0b788311
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e25a10ebfdeab6a24c5db324c0d9d3771feaa9b5
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="database-engine-developer-documentation"></a>データベース エンジンの開発者向けのドキュメント
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] には、データベース アプリケーションの開発、管理、および制御のための豊富なツールが用意されています。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [CLR &#40;共通言語ランタイム&#41; 統合のプログラミング概念](../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] での .NET Framework for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Windows の CLR (共通言語ランタイム) コンポーネントの統合について説明します。 つまり、[!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic .NET や [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C# などの .NET Framework 言語を使用して、ストアド プロシージャ、トリガー、ユーザー定義型、ユーザー定義関数、ユーザー定義集計、およびストリーミング テーブル値関数を記述できます。  
  
 [SQL Server Native Client プログラミング](../relational-databases/native-client/sql-server-native-client-programming.md)  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client を使用することで、MARS (複数のアクティブな結果セット)、UDT (ユーザー定義データ型)、クエリ通知、スナップショット分離、XML データ型のサポートなど、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の新機能を利用して既存のアプリケーションを強化したり、新しいアプリケーションを作成したりする方法について説明します。  
  
 [SQLXML 4.0 のプログラミング概念](../relational-databases/sqlxml/sqlxml-4-0-programming-concepts.md)  
 SQLXML 3.0 と同じ機能に加えて、[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] で導入された xml データ型などの新機能に対応するための更新を提供する SQLXML の最新バージョンについて説明します。  
  
 [構成管理用の WMI プロバイダーの概念](../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
 Microsoft 管理コンソール (MMC) および [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 構成マネージャー用の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 構成マネージャー スナップインと共に使用される、パブリッシュされたレイヤーについて説明します。 これにより、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 構成マネージャーから要求されたレジストリ操作を処理する API 呼び出しは、統一されたインターフェイスで操作できます。また、選択された [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] サービスに対して高度な制御および操作を行えます。  
  
 [WMI Provider for Server Events の概念](../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)  
 WMI (Windows Management Instrumentation) を使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスのイベントを監視する方法について説明します。  
  
 [SQL Server 管理オブジェクト &#40;SMO&#41; プログラミング ガイド](../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の管理に必要なあらゆる機能をプログラミングできるように設計されたオブジェクトの集まりである、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) について説明します。  
  
 [データベース エンジン拡張ストアド プロシージャ プログラミング](../relational-databases/database-engine-extended-stored-procedure-programming.md)  
 拡張ストアド プロシージャを使用して、C などのプログラミング言語でユーザー独自の外部ルーチンを作成する方法について説明します。  
  
 [データ コレクターのプログラミング](http://msdn.microsoft.com/library/53b4752b-055d-4716-b2bc-75b4cce84101)  
 Data Collector オブジェクト モデルについて説明します。  
  
 [例外メッセージ ボックスのプログラミング](http://msdn.microsoft.com/library/0b1ba514-6959-4e69-bfd2-3cf3c1ac4b9c)  
 アプリケーションに例外メッセージ ボックス プログラム インターフェイスを使用して、メッセージ エクスペリエンスを高い柔軟性で制御し、ユーザーが後で参照できるようにエラー メッセージを保存したり、メッセージのヘルプを表示したりできるようにする方法を説明します。  
  
## <a name="see-also"></a>参照  
 [Data Mining Programming (データ マイニングのプログラミング)](../analysis-services/data-mining-programming.md)   
 [Analysis Services Developer Documentation (Analysis Services の開発者向けドキュメント)](../analysis-services/analysis-services-developer-documentation.md)   
 [Integration Services Developer Documentation (Integration Services の開発者向けのドキュメント)](../integration-services/integration-services-developer-documentation.md)   
 [Replication Developer Documentation (レプリケーション開発者のドキュメント)](../relational-databases/replication/concepts/replication-developer-documentation.md)   
 [Reporting Services Developer Documentation (Reporting Services の開発者向けのドキュメント)](../reporting-services/reporting-services-developer-documentation.md)  
  
  
