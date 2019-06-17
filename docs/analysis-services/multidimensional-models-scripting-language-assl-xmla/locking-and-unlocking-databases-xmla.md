---
title: ロックとデータベース (XMLA) をロック解除 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1f827221a6334b0ff1daf523460562527c3a3f66
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63262068"
---
# <a name="locking-and-unlocking-databases-xmla"></a>データベースのロックおよびロック解除 (XMLA)
  ロックして、それぞれを使用してデータベースをロック解除することができます、[ロック](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)と[Unlock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) xml for Analysis (XMLA) コマンド。 通常、他の XMLA コマンドは、実行時にコマンドを完了させる必要に応じて、自動的にオブジェクトをロック/ロック解除します。 明示的にロックまたはなど、単一のトランザクション内で複数のコマンドを実行するデータベースのロックを解除することができます、[バッチ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla)コマンドから、他のアプリケーション データベースへの書き込みトランザクションをコミットするを防止します。  
  
## <a name="locking-databases"></a>データベースのロック  
 **ロック**コマンドが現在アクティブなトランザクションのコンテキスト内での共有または排他の使用のいずれかのオブジェクトをロックします。 オブジェクトをロックすると、そのロックが解除されるまでトランザクションはコミットできません。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 2 種類の共有ロックと排他ロックをサポートしています。 サポートされているロックの種類の詳細については[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を参照してください[Mode 要素&#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/mode-element-xmla)します。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、データベースに対するロックだけが可能です。 [オブジェクト](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)要素へのオブジェクト参照を含める必要があります、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース。 場合、**オブジェクト**要素が指定されていない場合は、**オブジェクト**要素は、データベース以外のオブジェクトを参照エラーが発生します。  
  
> [!IMPORTANT]  
>  データベース管理者またはサーバー管理者のみに明示的に発行できる、**ロック**コマンド。  
  
 他のコマンドに暗黙的に問題を**ロック**コマンドを[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース。 いずれかなど、データベースからデータまたはメタデータを読み取る操作[Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover)メソッドまたは[Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)メソッドを実行している、[ステートメント](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla)コマンドで、共有を暗黙的に発行データベースをロックします。 オブジェクトへのデータまたはメタデータの変更をコミットするトランザクションを[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]などのデータベース、 **Execute**メソッドを実行している、 [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)コマンドを暗黙的に排他ロックの問題、データベース。  
  
## <a name="unlocking-objects"></a>データベースのロック解除  
 **Unlock** コマンドは、現在アクティブなトランザクションのコンテキスト内で確立されたロックを解除します。  
  
> [!IMPORTANT]  
>  **Unlock** コマンドを明示的に発行できるのは、データベース管理者またはサーバー管理者だけです。  
  
 すべてのロックは、現在のトランザクションのコンテキスト内で保持されます。 現在のトランザクションがコミットまたはロールバックされると、そのトランザクション内で定義されたすべてのロックは自動的に解放されます。  
  
## <a name="see-also"></a>参照  
 [要素をロック&#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)   
 [要素のロック解除&#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)   
 [Analysis Services での XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
