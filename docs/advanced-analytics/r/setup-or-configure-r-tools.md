---
title: "R ツールのセットアップまたは構成 | Microsoft Docs"
ms.custom: 
ms.date: 01/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c04ae30-d391-4369-9742-d2b275e14c0d
caps.latest.revision: 9
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a3baf97a960d7e8f950bb6e9cd251550f4c4b942
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="setup-or-configure-r-tools"></a>R ツールのセットアップまたは構成
  Microsoft R Server では、R コードの開発とテストに必要となる、基本の R ライブラリ、ScaleR パッケージのセット、および標準 R ツールがすべて提供されます。 ただし、R 開発専用環境を使用したい場合は、多くの無料ツールも含め、使用できるものがいくつかあります。  
  
## <a name="basic-r-tools"></a>基本の R ツール  
 Microsoft R Server のインストールには追加のツールは必要ありません。R の*基本インストール*に含まれる標準 R ツールはすべて既定でインストールされるためです。

-   **RTerm**: R スクリプトを実行するためのコマンドライン ツール 
  
-   **RGui.exe**:  R のための単純な対話型エディター。コマンドライン引数は RGui.exe と RTerm で同じです。 
  
-   **RScript**: R スクリプトをバッチ モードで実行するためのコマンドライン ツール。  

これらのツールを見つけるには、R ライブラリの場所を確認してください。 これは、SQL Server R Services のみをインストールしたか、R Server (スタンドアロン) もインストールしたかによって異なります。 詳しくは、「[インストールされる内容と R パッケージの置かれる場所](https://msdn.microsoft.com/library/mt695941(sql.130).aspx#Anchor_1)」をご覧ください。

フォルダー `..\R_SERVER\bin\x64` の中を見てください。  

> [!TIP]  
>  R ツールの使用方法にお困りですか。 セットアップ フォルダー `C:\Program Files\Microsoft SQL Server\R_SERVER\doc` および `C:\Program Files\Microsoft SQL Server\R_SERVER\doc\manual` にドキュメントが含まれています。  
>   
>  または、**RGui** を開いて **[ヘルプ]** をクリックし、いずれかのオプションを選択してください。  

## <a name="microsoft-r-client"></a>Microsoft R Client

Microsoft R Client は無料でダウンロードでき、これを使用すると、Microsoft R Server または SQL Server R Services で簡単に実行できる R ソリューションを開発できます。 このオプションは、R Server (Enterprise Edition で使用可能) へのアクセス権を持たないデータ サイエンティストが、ScaleR を使用するソリューションを開発する際に役立ちます。 

別の R 開発環境 (R Tools for Visual Studio つまり RStudio など) を使用して ScaleR を使用する場合は、Microsoft R Client が R 実行可能ファイルとして使用されることを指定する必要があります。 こうすると、RevoScaleR パッケージと他の Microsoft R Server 機能に対する完全なアクセス権を得ることができます。ただし、パフォーマンスは制限されます。

また、R Client で提供されるツール (RGui や RTerm など) を使用して、スクリプトの実行や、アドホック R コードの作成や実行を行うこともできます。

[Microsoft R Client をインストールする](https://msdn.microsoft.com/microsoft-r/r-client-install)
  
##  <a name="bkmk_RTools"></a> R Tools for Visual Studio  

 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースを使用する際の利便性のために、[!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] を開発環境として使用することを検討してください。 [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] は Visual Studio の無料アドインです。Visual Studio のすべてのエディションで作動します。 Visual Studio では Python および F# 統合のサポートも提供されます。  

 インストール手順については、次を参照してください。 [R Tools for Visual Studio のインストール方法](https://docs.microsoft.com/visualstudio/rtvs/installation)です。

> [!TIP]
> 新しいパッケージをインストールする前に、どの R ランタイムが既定で使用されているかを確認します。 そうしないと、既定のライブラリの場所に新しい R パッケージをインストールしてしまい、R Server から新しいパッケージを見つけられなくなる可能性があります。


## <a name="rstudio"></a>RStudio

RStudio を使用する場合は、RevoScaleR ライブラリを使用するために追加の手順が必要です。
- Microsoft R Server または Microsoft R Client をインストールして必要なパッケージとライブラリを取得します。
- R Server ランタイムを使用する R パスを更新します。

詳しくは、「[Configure Your IDE](https://msdn.microsoft.com/microsoft-r/r-client-get-started#step-2-configure-your-ide)」(IDE の構成) をご覧ください。


## <a name="see-also"></a>参照  
 [スタンドアロン R Server の作成](../../advanced-analytics/r-services/create-a-standalone-r-server.md)   
 [Microsoft R Server の概要 &#40;スタンドアロン&#41;](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)  
  
  

