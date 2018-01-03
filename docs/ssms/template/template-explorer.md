---
title: "テンプレート エクスプローラー | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-templates
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.templates.explorer.f1
- sql13.wb.templates.f1
helpviewer_keywords:
- templates [SQL Server]
- SQL Server Management Studio [SQL Server], Template Explorer
- Template Explorer
- templates [Transact-SQL]
- templates [SQL Server], Template Explorer
ms.assetid: b9ee55c5-bb44-4f76-90ac-792d8d83b4c8
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: cd3d984df93312d1eb58bbef7e4eea92dc758a1e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="template-explorer"></a>テンプレート エクスプローラー
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] にはさまざまなテンプレートがあります。 テンプレートは、データベース内のオブジェクトを簡単に作成するための SQL スクリプトを含む、定型的なファイルです。 テンプレート エクスプローラーを初めて開いたときには、テンプレートのコピーが C:\Users の AppData\Roaming\Microsoft\SQL Server Management Studio\130\Templates にあるユーザーのフォルダーに配置されています。  
  
使用できるテンプレートをテンプレート エクスプローラーで参照し、テンプレートを開いて、コードをコード エディター ウィンドウに読み込むことができます。 また、カスタム テンプレートを作成することもできます。  
  
## <a name="benefits-of-templates"></a>テンプレートの利点  
テンプレートはソリューション、プロジェクト、および各種のコード エディターに対して使用できます。 テンプレートは、データベース、テーブル、ビュー、インデックス、ストアド プロシージャ、トリガー、統計、関数のようなオブジェクトを作成するために使用できます。 さらに、拡張プロパティ、リンク サーバー、ログイン、ロール、ユーザーを作成してサーバーを管理するために役立つテンプレートや、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)]のテンプレートもあります。  
  
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] で提供されるテンプレート スクリプトにはパラメーターを指定できるので、コードをカスタマイズできます。 テンプレートを開くときに、 **[テンプレート パラメーターの置換]** ダイアログ ボックスでスクリプトに値を挿入します。  
  
頻繁に実行するタスクについては、カスタム テンプレートを作成します。 カスタム スクリプトは、既存のフォルダーに入れるか、新しいフォルダーを作成して整理します。  
  
[!INCLUDE[ssDE](../../includes/ssde_md.md)] クエリ エディターもコード スニペットをサポートしており、スクリプト内の特定の場所を右クリックして、そこにコード スニペットを挿入できます。  
  
## <a name="related-tasks"></a>Related Tasks  
テンプレートの基礎知識については、次の各トピックを参照してください。  
  
|**Description**|**トピック**|  
|-------------------|-------------|  
|テンプレートからコード エディター ウィンドウにコードを読み込む方法について説明します。|[テンプレートを開く](../../ssms/template/open-a-template.md)|  
|コード エディターでテンプレートを開いてからテンプレート パラメーターの値を置換する方法について説明します。|[[テンプレート パラメーターの置換]](../../ssms/template/replace-template-parameters.md)|  
  
