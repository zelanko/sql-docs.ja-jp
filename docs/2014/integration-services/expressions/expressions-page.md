---
title: '[式] ページ | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.expressionspage.f1
helpviewer_keywords:
- Expressions Page dialog box
ms.assetid: c9016ec6-11c1-4ebd-b2a7-0fa6631fd9e4
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: a266929860877c960c656033c41715154b6e2736
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164340"
---
# <a name="expressions-page"></a>[式] ページ
  **[式]** ページを使用すると、プロパティ式を編集でき、 **[プロパティ式エディター]** ダイアログ ボックスや **[式ビルダー]** ダイアログ ボックスにアクセスできます。  
  
 プロパティ式は、パッケージが実行されたときに、プロパティの値を更新します。 プロパティ式は、パッケージ、タスク、コンテナー、接続マネージャーに加えて、一部のデータ フロー コンポーネントのプロパティでも使用できます。 式が評価されると、その結果が、パッケージおよびパッケージ オブジェクトの構成時にプロパティに設定した値の代わりに使用されます。 式には、変数と、式の言語で提供されている関数および演算子を含めることができます。 たとえば、文字列 "Weather forecast for " を含む変数の値と、GETDATE() 関数によって返される結果を連結して、文字列 "Weather forecast for 4/5/2006" を作成することにより、メール送信タスクの件名行を生成することができます。  
  
 式を作成して、プロパティ式の使用に関する詳細についてを参照してください。 [Integration Services &#40;SSIS&#41;式](integration-services-ssis-expressions.md)と[使用 Property Expressions in Packages](use-property-expressions-in-packages.md)です。  
  
## <a name="options"></a>および  
 **[Expressions (...)]**  
 [...] をクリックすると、 **[プロパティ式エディター]** ダイアログ ボックスが表示されます。 詳細については、「[プロパティ式エディター](property-expressions-editor.md)」を参照してください。  
  
 **\<プロパティ名>**  
 [...] をクリックすると、 **[式ビルダー]** ダイアログ ボックスが表示されます。 詳細については、「 [式ビルダー](expression-builder.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Integration Services &#40;SSIS&#41;変数](../integration-services-ssis-variables.md)   
 [システム変数](../system-variables.md)   
 [Integration Services &#40;です。SSIS&#41; 式](integration-services-ssis-expressions.md)  
  
  