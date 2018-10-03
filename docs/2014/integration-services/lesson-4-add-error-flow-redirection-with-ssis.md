---
title: 'レッスン 4: エラー フロー リダイレクションの追加 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 0c8dbda2-75e3-4278-9b4e-dcd220c92522
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 39fdc04590f6a5656e902794f4965ef53f21bfad
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48154432"
---
# <a name="lesson-4-adding-error-flow-redirection"></a>レッスン 4 : エラー フロー リダイレクションの追加
  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] には、変換できないデータの処理方法を、コンポーネントごと、および列ごとに指定できる機能があります。これにより、変換プロセスで発生するエラーを処理することができます。 特定の列で発生したエラーは無視し、変換に失敗した行全体をリダイレクトできます。または、この操作をコンポーネント単位で行うこともできます。 既定の構成では、エラーの発生時に [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のすべてのコンポーネントが変換に失敗したものと見なされます。 つまり、1 つのコンポーネントの変換が失敗すると、パッケージの変換が失敗されたものと見なされ、以降の処理が中断されます。  
  
 パッケージ全体の変換を中断する代わりに、変換エラーが発生したときに潜在的なエラー処理を行うように構成する方法があります。 エラーを無視してパッケージが確実に実行されるように設定することもできますが、多くの場合、失敗した行を別の処理フローにリダイレクトした方がよい結果が得られます。退避させたデータおよびエラーは後で検証し、再変換できます。  
  
 このレッスンで開発したパッケージのコピーを作成します[レッスン 3: 追加のログ記録](lesson-3-add-logging-with-ssis.md)します。 この新しいパッケージを使用し、壊れたサンプル データ ファイルを作成します。 この破損ファイルは、パッケージを実行するときに変換エラーを発生させます。  
  
 エラー データを処理するには、フラット ファイルの変換先を追加および構成し、Lookup Currency Key 変換で参照値が見つからなかった行をファイルに書き込むようにします。  
  
 また、エラー データをファイルに書き込む前に、エラーの説明を取得するスクリプトを含むスクリプト コンポーネントを追加し、 その後 Lookup Currency Key 変換を再構成して、処理できなかったデータをスクリプト変換にリダイレクトするようにします。  
  
> [!IMPORTANT]  
>  このチュートリアルには、 **AdventureWorksDW2012** サンプル データベースが必要です。 インストールおよび展開方法の詳細について**AdventureWorksDW2012**を参照してください[Reporting Services 製品サンプル codeplex のプロジェクト](http://go.microsoft.com/fwlink/p/?LinkId=526910)します。  
  
## <a name="tasks-in-lesson"></a>レッスンでの作業  
 このレッスンの内容は次のとおりです。  
  
-   [手順 1: レッスン 3 のパッケージのコピー](lesson-4-1-copying-the-lesson-3-package.md)  
  
-   [手順 2: 破損ファイルの作成](lesson-4-2-creating-a-corrupted-file.md)  
  
-   [手順 3: エラー フロー リダイレクトの追加](lesson-4-3-adding-error-flow-redirection.md)  
  
-   [手順 4: フラット ファイル変換先の追加](lesson-4-4-adding-a-flat-file-destination.md)  
  
-   [手順 5: レッスン 4 のチュートリアル パッケージのテスト](lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>レッスンの開始  
 [手順 1: レッスン 3 のパッケージのコピー](lesson-4-1-copying-the-lesson-3-package.md)  
  
  
