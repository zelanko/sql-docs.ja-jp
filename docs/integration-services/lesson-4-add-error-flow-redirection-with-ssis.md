---
title: "レッスン 4: SSIS によるエラー フロー リダイレクトの追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 0c8dbda2-75e3-4278-9b4e-dcd220c92522
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cfe3634566a7ede28e3c1f5640cfe6e4caa1c351
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="lesson-4-add-error-flow-redirection-with-ssis"></a>レッスン 4: SSIS でエラー フロー リダイレクションを追加する
[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] には、変換できないデータの処理方法を、コンポーネントごと、および列ごとに指定できる機能があります。これにより、変換プロセスで発生するエラーを処理することができます。 特定の列で発生したエラーは無視し、変換に失敗した行全体をリダイレクトできます。または、この操作をコンポーネント単位で行うこともできます。 既定の構成では、エラーの発生時に [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のすべてのコンポーネントが変換に失敗したものと見なされます。 つまり、1 つのコンポーネントの変換が失敗すると、パッケージの変換が失敗されたものと見なされ、以降の処理が中断されます。  
  
パッケージ全体の変換を中断する代わりに、変換エラーが発生したときに潜在的なエラー処理を行うように構成する方法があります。 エラーを無視してパッケージが確実に実行されるように設定することもできますが、多くの場合、失敗した行を別の処理フローにリダイレクトした方がよい結果が得られます。退避させたデータおよびエラーは後で検証し、再変換できます。  
  
このレッスンでは、「 [レッスン 3: SSIS でのログ記録の追加](../integration-services/lesson-3-add-logging-with-ssis.md)」で作成したパッケージのコピーを作成します。 この新しいパッケージを使用し、壊れたサンプル データ ファイルを作成します。 この破損ファイルは、パッケージを実行するときに変換エラーを発生させます。  
  
エラー データを処理するには、フラット ファイルの変換先を追加および構成し、Lookup Currency Key 変換で参照値が見つからなかった行をファイルに書き込むようにします。  
  
また、エラー データをファイルに書き込む前に、エラーの説明を取得するスクリプトを含むスクリプト コンポーネントを追加し、 その後 Lookup Currency Key 変換を再構成して、処理できなかったデータをスクリプト変換にリダイレクトするようにします。  
  
> [!IMPORTANT]  
> このチュートリアルには、 **AdventureWorksDW2012** サンプル データベースが必要です。 **AdventureWorksDW2012**, [Reporting Services Product Samples on CodePlex (CodePlex の Reporting Services 製品サンプル)](http://go.microsoft.com/fwlink/p/?LinkID=526910)」を参照してください。  
  
## <a name="tasks-in-lesson"></a>レッスンでの作業  
このレッスンの内容は次のとおりです。  
  
-   [手順 1: レッスン 3 のパッケージのコピー](../integration-services/lesson-4-1-copying-the-lesson-3-package.md)  
  
-   [手順 2: 破損ファイルの作成](../integration-services/lesson-4-2-creating-a-corrupted-file.md)  
  
-   [手順 3: エラー フロー リダイレクトの追加](../integration-services/lesson-4-3-adding-error-flow-redirection.md)  
  
-   [手順 4: フラット ファイル変換先の追加](../integration-services/lesson-4-4-adding-a-flat-file-destination.md)  
  
-   [手順 5: レッスン 4 のチュートリアル パッケージのテスト](../integration-services/lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>レッスンの開始  
[手順 1: レッスン 3 のパッケージのコピー](../integration-services/lesson-4-1-copying-the-lesson-3-package.md)  
  
  
  

