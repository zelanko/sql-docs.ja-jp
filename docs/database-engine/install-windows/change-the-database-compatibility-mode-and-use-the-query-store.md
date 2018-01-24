---
title: "データベース互換性モードの変更とクエリ ストアの使用 | Microsoft Docs"
ms.custom: 
ms.date: 07/21/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: install-windows
ms.reviewer: 
ms.suite: sql
ms.technology: setup-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- query plans [SQL Server], migrating
- upgrading SQL Server, migrating query plans
- plan guides [SQL Server], migrating query plans
ms.assetid: 7e02a137-6867-4f6a-a45a-2b02674f7e65
caps.latest.revision: "19"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0f4d36ec95ab9d6a1a714b597331bd4d24bb9e85
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="change-the-database-compatibility-mode-and-use-the-query-store"></a>データベース互換性モードの変更とクエリ ストアの使用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server 2016 および SQL Server 2017 では、一部の変更は、データベースの DATABASE_COMPATIBILITY レベルが変更された場合にのみ有効になります。 これは、次の理由のためです。  
  
- アップグレードは一方向の操作である (ファイル形式をダウン グレードできない) ため、データベース内で新機能を有効にする操作を別の操作に分離することが重要です。  設定を前の DATABASE_COMPATIBILITY レベルに戻すことができます。  新しいモデルでは、停止期間中に発生する処理の数が減ります。  
  
- クエリ プロセッサに対する変更は、複雑な影響をもたらす可能性があります。  システムに対する "良い" 変更は、ほとんどのユーザーには有益であっても、その他のユーザーにとって重要なクエリで許容できない回帰を引き起こす可能性があります。  アップグレード プロセスからこのロジックを分離すると、クエリ ストアなどの機能は、プラン選択の回帰を迅速に緩和し、さらには実稼働サーバーで完全に回避できます。  
  
> [!NOTE]  
>  アップグレード前のユーザー データベースの互換性レベルが 100 以上の場合は、アップグレード後も互換性レベルは変わりません。 アップグレード前の互換性レベルが 90 の場合、アップグレードされたデータベースの互換性レベルは 100 に設定されます。これは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]でサポートされている下限の互換性レベルです。 tempdb、model、msdb、および Resource データベースの互換性レベルは、アップグレード後に現在の互換性レベルに設定されます。 master システム データベースは、アップグレード前の互換性レベルを保持します。 
  
 新しいクエリ プロセッサの機能を有効にするためのアップグレード プロセスは、製品のリリース後のサービス モデルに関連付けられます。  それらの修正プログラムの一部は、トレース フラグ 4199 でリリースされます。  修正プログラムを必要とするユーザーは、他のユーザーにとって予期しない回帰を引き起こすことなくそれらの修正プログラムを適用できます。  クエリ プロセッサの修正プログラムのリリース後のサービス モデルは、 [ここ](https://support.microsoft.com/en-us/kb/974006)に記載されています。 SQL Server 2016 以降では、新しい互換性レベルに移行した場合、4199 トレース フラグは不要になります。これは、それらの修正プログラムは最新の互換レベルで既定で有効になっているためです。  そのため、アップグレード プロセスの一環として、アップグレード プロセスが完了したら、4199 が無効になっていることを検証することが重要です。  
  
 クエリ プロセッサを最新バージョンのコードにアップグレードするための推奨ワークフローは次のとおりです。  
  
1.  データベース互換性レベルを変更せずに (前のレベルを維持して)、データベースを SQL Server 2016 にアップグレードします。  
  
2.  データベースでクエリ ストアを有効にします。 クエリ ストアの有効化と使用に関する詳細については、「 [Monitoring Performance By Using the Query Store](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)」を参照してください。  
  
3.  ワークロードの代表データを収集するために、十分な時間待機します。  
  
4.  データベースの互換性レベルを現在の互換性レベルに変更します。 

   >[!NOTE]
   >最新の互換性レベルは、SQL Server のバージョンによって異なります。
   >- SQL Server 2016: 130
   >- SQL Server 2017: 140

5. SQL Server Management Studio を使用して、互換性レベルの変更後に特定のクエリのパフォーマンスの回帰があるかどうかを評価します。
  
6.  回帰がある場合は、クエリ ストアで前のプランを強制的に適用します。  
  
7.  クエリ プランの適用に失敗した場合、またはパフォーマンスが依然として十分ではない場合は、互換性レベルを前の設定に戻し、Microsoft カスタマー サポートにお問い合わせください。  
  
## <a name="see-also"></a>参照  
 [データベースの互換性レベルの表示または変更](../../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md)  
  
  
