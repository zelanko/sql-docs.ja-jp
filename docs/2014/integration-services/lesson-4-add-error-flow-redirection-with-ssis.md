---
title: 'レッスン 4: エラーフローリダイレクトの追加 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0c8dbda2-75e3-4278-9b4e-dcd220c92522
author: janinezhang
ms.author: janinez
ms.openlocfilehash: a97a07c4854fc1e25913aff7b6e966be79032e86
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84951562"
---
# <a name="lesson-4-adding-error-flow-redirection"></a>レッスン 4:エラー フロー リダイレクトの追加
  変換プロセスで発生する可能性のあるエラーを処理するために、には、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 変換できないデータを処理する方法を、コンポーネントごと、および列ごとに決定する機能が用意されています。 特定の列で発生したエラーは無視し、変換に失敗した行全体をリダイレクトできます。または、この操作をコンポーネント単位で行うこともできます。 既定の構成では、エラーの発生時に [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のすべてのコンポーネントが変換に失敗したものと見なされます。 つまり、1 つのコンポーネントの変換が失敗すると、パッケージの変換が失敗されたものと見なされ、以降の処理が中断されます。  
  
 パッケージ全体の変換を中断する代わりに、変換エラーが発生したときに潜在的なエラー処理を行うように構成する方法があります。 エラーを無視してパッケージが確実に実行されるように設定することもできますが、多くの場合、失敗した行を別の処理フローにリダイレクトした方がよい結果が得られます。退避させたデータおよびエラーは後で検証し、再変換できます。  
  
 このレッスンでは、 [「レッスン 3: ログの追加](lesson-3-add-logging-with-ssis.md)」で開発したパッケージのコピーを作成します。 この新しいパッケージを使用し、壊れたサンプル データ ファイルを作成します。 この破損ファイルは、パッケージを実行するときに変換エラーを発生させます。  
  
 エラー データを処理するには、フラット ファイルの変換先を追加および構成し、Lookup Currency Key 変換で参照値が見つからなかった行をファイルに書き込むようにします。  
  
 また、エラー データをファイルに書き込む前に、エラーの説明を取得するスクリプトを含むスクリプト コンポーネントを追加し、 その後 Lookup Currency Key 変換を再構成して、処理できなかったデータをスクリプト変換にリダイレクトするようにします。  
  
> [!IMPORTANT]  
>  このチュートリアルには、 **AdventureWorksDW2012** サンプル データベースが必要です。 **AdventureWorksDW2012**をインストールしてデプロイする方法の詳細については、 [CodePlex の Reporting Services Product Samples プロジェクト](https://go.microsoft.com/fwlink/p/?LinkId=526910)を参照してください。  
  
## <a name="tasks-in-lesson"></a>レッスンでの作業  
 このレッスンの内容は次のとおりです。  
  
-   [手順 1:レッスン 3 のパッケージのコピー](lesson-4-1-copying-the-lesson-3-package.md)  
  
-   [手順 2:破損ファイルの作成](lesson-4-2-creating-a-corrupted-file.md)  
  
-   [手順 3:エラー フロー リダイレクトの追加](lesson-4-3-adding-error-flow-redirection.md)  
  
-   [手順 4:フラット ファイル変換先の追加](lesson-4-4-adding-a-flat-file-destination.md)  
  
-   [手順 5:レッスン 4 のチュートリアル パッケージのテスト](lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>レッスンの開始  
 [手順 1:レッスン 3 のパッケージのコピー](lesson-4-1-copying-the-lesson-3-package.md)  
  
  
