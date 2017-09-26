---
title: "Integration Services 言語リファレンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
ms.assetid: c67b72f1-0a1e-42f0-878a-84e85efc915b
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9fe4120f8a5dc93517e8eb35b13e7fe5252be6b6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="integration-services-language-reference"></a>Integration Services 言語リファレンス
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このセクションの内容について説明します、[!INCLUDE[tsql](../includes/tsql-md.md)]を管理するための API[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]のインスタンスに配置されているプロジェクト[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]です。  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]呼ばれるデータベース内のオブジェクト、設定、およびオペレーション データを格納、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]カタログ。 既定の名前、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]カタログには SSISDB します。 カタログに格納されているオブジェクトには、プロジェクト、パッケージ、パラメーター、環境、および操作履歴があります。  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] カタログは、ユーザーに表示されない内部テーブルにデータを格納します。 ただし、必要な情報は、パブリック ビューに対してクエリを実行することで公開されます。 カタログの一般的なタスクを実行するために使用できる一連のストアド プロシージャも用意されています。  
  
 通常、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] を開くことによって、カタログの [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] オブジェクトを管理します。 ただし、データベース ビューとストアド プロシージャを直接使用することも、マネージ API を呼び出すカスタム コードを記述することもできます。 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]マネージ API は、ビューに対してクエリし、多くのタスクを実行するには、このセクションで説明されているストアド プロシージャを呼び出します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ビュー (&) #40";"Integration Services カタログ"&"#41;](../integration-services/system-views/views-integration-services-catalog.md)  
 検査するビューをクエリ[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]オブジェクト、設定、およびオペレーション データ。  
  
 [ストアド プロシージャ &#40; Integration Services カタログ"&"#41;](../integration-services/system-stored-procedures/stored-procedures-integration-services-catalog.md)  
 追加、削除、または変更するには、ストアド プロシージャを呼び出す[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]オブジェクトおよび設定します。  
  
 [関数 &#40;Integration Services カタログ&#41;](http://msdn.microsoft.com/library/9f2aec85-3d4c-415f-b1f8-8328a60b1c7f)  
 管理する関数を呼び出す[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]プロジェクト。  
  
  
