---
title: "ロックおよびロック解除データベース (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- locking [XML for Analysis]
- XML for Analysis, locking
- XMLA, locking
- unlocking objects
ms.assetid: 451afa58-ce03-4ecc-8dd3-9e7e8559b5f1
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 47b88aa52aba52f2919d41cba462323e5b061bdf
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="locking-and-unlocking-databases-xmla"></a>データベースのロックおよびロック解除 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]ロックして、それぞれを使用して、データベースをロック解除することができます、[ロック](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)と[Unlock](../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md) xml for Analysis (XMLA) コマンド。 通常、他の XMLA コマンドは、実行時にコマンドを完了させる必要に応じて、自動的にオブジェクトをロック/ロック解除します。 明示的にロックしたりなど、単一のトランザクション内で複数のコマンドを実行するデータベースのロックを解除、[バッチ](../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)他のアプリケーション データベースへの書き込みトランザクションをコミットするを防止しながら、コマンド。  
  
## <a name="locking-databases"></a>データベースのロック  
 **ロック**コマンドが現在アクティブなトランザクションのコンテキスト内で、共有、または排他的に使用のいずれかのオブジェクトをロックします。 オブジェクトをロックすると、そのロックが解除されるまでトランザクションはコミットできません。 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、共有ロックと排他ロックの 2 つの種類をサポートします。 サポートされているロックの種類の詳細については[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を参照してください[Mode 要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-properties/mode-element-xmla.md).  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、データベースに対するロックだけが可能です。 [オブジェクト](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)要素へのオブジェクト参照を含める必要があります、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース。 場合、**オブジェクト**要素が指定されていない場合は、**オブジェクト**要素を参照し、データベース以外のオブジェクト、エラーが発生します。  
  
> [!IMPORTANT]  
>  データベース管理者またはサーバー管理者のみに明示的に発行できる、**ロック**コマンド。  
  
 他のコマンドの問題では暗黙的に、**ロック**コマンドを[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース。 いずれかなど、データベースからデータまたはメタデータを読み取る操作[Discover](../../analysis-services/xmla/xml-elements-methods-discover.md)メソッドまたは[Execute](../../analysis-services/xmla/xml-elements-methods-execute.md)実行されているメソッド、[ステートメント](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)コマンドで、共有を暗黙的に発行データベースに対してロックします。 オブジェクトへのデータまたはメタデータの変更をコミットするすべてのトランザクション、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]などのデータベース、 **Execute**実行されているメソッド、 [Alter](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)コマンドでの排他ロックを暗黙的に発行しますデータベースです。  
  
## <a name="unlocking-objects"></a>データベースのロック解除  
 **Unlock** コマンドは、現在アクティブなトランザクションのコンテキスト内で確立されたロックを解除します。  
  
> [!IMPORTANT]  
>  **Unlock** コマンドを明示的に発行できるのは、データベース管理者またはサーバー管理者だけです。  
  
 すべてのロックは、現在のトランザクションのコンテキスト内で保持されます。 現在のトランザクションがコミットまたはロールバックされると、そのトランザクション内で定義されたすべてのロックは自動的に解放されます。  
  
## <a name="see-also"></a>参照  
 [Lock 要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)   
 [要素 &#40; をロック解除します。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)   
 [Analysis Services での XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
