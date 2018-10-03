---
title: '[式] ページ | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.expressionspage.f1
helpviewer_keywords:
- Expressions Page dialog box
ms.assetid: c9016ec6-11c1-4ebd-b2a7-0fa6631fd9e4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: eb12bb684753a5d965054e361f8b0b23ebf7802d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48150472"
---
# <a name="expressions-page"></a>[式] ページ
  **[式]** ページを使用すると、プロパティ式を編集でき、 **[プロパティ式エディター]** ダイアログ ボックスや **[式ビルダー]** ダイアログ ボックスにアクセスできます。  
  
 プロパティ式は、パッケージが実行されたときに、プロパティの値を更新します。 プロパティ式は、パッケージ、タスク、コンテナー、接続マネージャーに加えて、一部のデータ フロー コンポーネントのプロパティでも使用できます。 式が評価されると、その結果が、パッケージおよびパッケージ オブジェクトの構成時にプロパティに設定した値の代わりに使用されます。 式には、変数と、式の言語で提供されている関数および演算子を含めることができます。 たとえば、文字列 "Weather forecast for " を含む変数の値と、GETDATE() 関数によって返される結果を連結して、文字列 "Weather forecast for 4/5/2006" を作成することにより、メール送信タスクの件名行を生成することができます。  
  
 詳細については、式の作成とプロパティ式を使用して、参照してください。 [Integration Services &#40;SSIS&#41;式](integration-services-ssis-expressions.md)と[パッケージでプロパティ式を使用して](use-property-expressions-in-packages.md)します。  
  
## <a name="options"></a>および  
 **[Expressions (...)]**  
 [...] をクリックすると、 **[プロパティ式エディター]** ダイアログ ボックスが表示されます。 詳細については、「[プロパティ式エディター](property-expressions-editor.md)」を参照してください。  
  
 **\<プロパティ名>**  
 [...] をクリックすると、 **[式ビルダー]** ダイアログ ボックスが表示されます。 詳細については、「 [式ビルダー](expression-builder.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Integration Services &#40;SSIS&#41;変数](../integration-services-ssis-variables.md)   
 [システム変数](../system-variables.md)   
 [Integration Services &#40;です。SSIS&#41; 式](integration-services-ssis-expressions.md)  
  
  
