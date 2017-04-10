---
title: "SQL Server 2016 における Analysis Services 機能の動作の変更 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 92ebd5cb-afb6-4b62-968f-39f5574a452b
caps.latest.revision: 17
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 17
---
# SQL Server 2016 における Analysis Services 機能の動作の変更
  *動作の変更* の影響は、現在のバージョンの SQL Server の機能や操作方法が、以前のバージョンの SQL Server とは異なることに表れます。  
  
 製品動作の変更の例として、既定値の変更、アップグレードまたは復元機能を完了するために必要な手動の構成、または既存の機能の新しい実装などがあります。  
  
 このリリースで変更される機能の動作は、今のところ既存のモデルやアップグレード後のコードを破壊することはありませんが、ここに一覧を示します。  
  
> [!NOTE]  
>  *動作の変更*とは対照的に、 *重大な変更* では、サーバー、クライアント ツール、またはモデルをアップグレードした後に、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] と統合されたデータ モデルやアプリケーションが実行されることを防ぎます。 この一覧については、「[SQL Server 2016 の Analysis Services 機能における重大な変更](../analysis-services/breaking-changes-to-analysis-services-features-in-sql-server-2016.md)」を参照してください。  
  
## SharePoint モードの Analysis Services  
 インストール後のタスクとしての Power Pivot 構成ウィザードの実行は不要になりました。 これは、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の現在の [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] リリースからモデルを読み込む、サポートされているすべてのバージョンの SharePoint に該当します。  
  
## 表形式モデルの DirectQuery モード  
 *DirectQuery* は、表形式モデル用のデータ アクセス モードです。ここでは、クエリ実行はリアルタイムで結果セットを取得して、バックエンド リレーショナル データベースで実行されます。 通常は、メモリに収まらない非常に大規模なデータセットや、データが揮発性で、表形式モデルに対するクエリで返された最新のデータが必要な場合に使用されます。  
  
 DirectQuery は、過去数回のリリースではデータ アクセス モードとして存在します。 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]では、表形式モデルを互換性レベル 1200 と見なして、実装がわずかに変更されています。 DirectQuery の制限は、以前よりも少なくなりました。 また、さまざまなデータベース プロパティもあります。  
  
 既存の表形式モデルで DirectQuery を使用している場合、モデルを現在の互換性レベル 1100 または 1103 に維持して、それらのレベルで実装された DirectQuery として使用し続けることができます。 または、1200 にアップグレードして、このリリースの [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]の DirectQuery に対して作成された拡張機能から利点を得ることもできます。  
  
 以前の互換性レベルの設定には、新しい互換性レベル 1200 に対応する設定がないため、DirectQuery モデルのインプレース アップグレードはありません。 DirectQuery モードで実行する既存の表形式モデルがある場合、SQL Server Data Tools でモデルを開いて、DirectQuery をオフにし、 **互換性レベル** プロパティを 1200 に設定して、表形式モデル 1200 用に定義された DirectQuery プロパティを再構成する必要があります。 詳細については、「[DirectQuery モード &#40;SSAS テーブル&#41;](../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)」を参照してください。  
  
## 参照  
 [旧バージョンとの互換性_削除](../Topic/Backward%20Compatibility_deleted.md)   
 [SQL Server 2016 の Analysis Services 機能における重大な変更](../analysis-services/breaking-changes-to-analysis-services-features-in-sql-server-2016.md)   
 [Analysis Services での表形式モデルの互換性レベル](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [SQL Server Data Tools のダウンロード](https://msdn.microsoft.com/en-us/library/mt204009.aspx)  
  
  