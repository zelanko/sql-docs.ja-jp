---
title: テンプレート エクスプローラー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.wb.templates.f1
- sql12.swb.templates.explorer.f1
helpviewer_keywords:
- templates [SQL Server]
- SQL Server Management Studio [SQL Server], Template Explorer
- Template Explorer
- templates [Transact-SQL]
- templates [SQL Server], Template Explorer
ms.assetid: b9ee55c5-bb44-4f76-90ac-792d8d83b4c8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cba129b4c9de133d4c1c2283b5d163a16e191c47
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48225592"
---
# <a name="template-explorer"></a>テンプレート エクスプローラー
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にはさまざまなテンプレートがあります。 テンプレートは、データベース内のオブジェクトを簡単に作成するための SQL スクリプトを含む、定型的なファイルです。 テンプレート エクスプローラーを初めて開いたときには、テンプレートのコピーが C:\Users の AppData\Roaming\Microsoft\SQL Server Management Studio\120\Templates にあるユーザーのフォルダーに配置されています。  
  
 使用できるテンプレートをテンプレート エクスプローラーで参照し、テンプレートを開いて、コードをコード エディター ウィンドウに読み込むことができます。 また、カスタム テンプレートを作成することもできます。  
  
## <a name="benefits-of-templates"></a>テンプレートの利点  
 テンプレートはソリューション、プロジェクト、および各種のコード エディターに対して使用できます。 テンプレートは、データベース、テーブル、ビュー、インデックス、ストアド プロシージャ、トリガー、統計、関数のようなオブジェクトを作成するために使用できます。 さらに、拡張プロパティ、リンク サーバー、ログイン、ロール、ユーザーを作成してサーバーを管理するために役立つテンプレートや、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のテンプレートもあります。  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で提供されるテンプレート スクリプトにはパラメーターを指定できるので、コードをカスタマイズできます。 テンプレートを開くときに、 **[テンプレート パラメーターの置換]** ダイアログ ボックスでスクリプトに値を挿入します。  
  
 頻繁に実行するタスクについては、カスタム テンプレートを作成します。 カスタム スクリプトは、既存のフォルダーに入れるか、新しいフォルダーを作成して整理します。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターもコード スニペットをサポートしており、スクリプト内の特定の場所を右クリックして、そこにコード スニペットを挿入できます。  
  
## <a name="related-tasks"></a>Related Tasks  
 テンプレートの基礎知識については、次の各トピックを参照してください。  
  
|**Description**|**トピック**|  
|---------------------|---------------|  
|テンプレートからコード エディター ウィンドウにコードを読み込む方法について説明します。|[テンプレートを開く](open-a-template.md)|  
|コード エディターでテンプレートを開いてからテンプレート パラメーターの値を置換する方法について説明します。|[[テンプレート パラメーターの置換]](replace-template-parameters.md)|  
  
  
