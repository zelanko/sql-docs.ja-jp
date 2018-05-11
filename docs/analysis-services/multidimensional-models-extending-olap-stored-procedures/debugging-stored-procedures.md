---
title: ストアド プロシージャのデバッグ |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6aecd65eb6b41b6b573bc7c4c13c3eb16b0dc2e9
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="debugging-stored-procedures"></a>デバッグ系のストアド プロシージャ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のストアド プロシージャは、実際には C# (あるいは他の CLR または COM 言語) で作成されている CLR または COM ライブラリ (通常は DLL) です。 このため、ストアド プロシージャのデバッグは、Visual Studio デバッグ環境で他のアプリケーションをデバッグする作業とほとんど同じになります。 Visual Studio 開発環境でのストアド プロシージャのデバッグは、統合されたデバッグ機能を使用します。 これらの機能を使用すると、プロシージャ内のさまざまな場所で停止し、メモリやレジスタの値を調査し、変数を変更し、メッセージ トラフィックを観察し、コードの動作を詳細にわたって確認することができます。  
  
### <a name="to-debug-a-stored-procedure"></a>ストアド プロシージャをデバッグするには  
  
1.  DLL の作成に使用したプロジェクトを Visual Studio で開きます。  
  
2.  デバッグするプロシージャに対応するメソッドまたは関数内にブレークポイントを作成します。  
  
3.  Visual Studio を使用して、ストアド プロシージャ DLL のデバッグ ビルドを作成します。  
  
4.  DLL をサーバーに配置します。 DLL をサーバーに配置の詳細については、次を参照してください。[ストアド プロシージャの作成](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/creating-stored-procedures.md)です。  
  
5.  テストするストアド プロシージャを呼び出すアプリケーションが必要です。 このようなアプリケーションを用意していない場合は、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の MDX クエリ エディターを使用して、テストするストアド プロシージャを呼び出す MDX クエリを作成できます。  
  
6.  Visual Studio で、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロセス (Msmdsrv.exe) にアタッチします。  
  
    1.  **デバッグ**] メニューの [選択**アタッチ toProcess**です。  
  
    2.  **アタッチ toProcess**ダイアログ ボックスで、**プロセスのすべてのユーザーを表示する**です。  
  
    3.  **選択可能なプロセス**一覧、**プロセス**列で、をクリックして**Msmdsrv.exe**です。 サーバーで [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスが複数実行されている場合は、使用するインスタンスの ID を使用してプロセスを識別する必要があります。  
  
    4.  **にアタッチ**テキスト ボックスで、適切なプログラムの種類が選択されているかどうかを確認します。 CLR dll の場合は、**選択**、順にクリックして**コードの種類をデバッグ**、をクリックして**マネージ**、をクリックして **[ok]** です。 COM dll の場合は、**選択**、順にクリックして**コードの種類をデバッグ**、をクリックして**ネイティブ**、をクリックして **[ok]** です。  
  
    5.  をクリックして**アタッチ**です。  
  
7.  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で、ストアド プロシージャを呼び出すプログラムまたは MDX スクリプトを起動します。 デバッガーは、ブレークポイントを含む行に達すると停止します。 ウォッチ ウィンドウで変数を評価し、ロケールを表示し、コードをステップ実行できます。  
  
 ライブラリを正しくデバッグできない場合は、対応するプログラム データベース (PDB) ファイルがサーバーの配置場所にコピーされていることを確認してください。 このファイルが登録または配置中にコピーされなかった場合には、DLL と同じ場所に手動でコピーする必要があります。 ネイティブ コード (COM DLL) の場合、PDB ファイルは \debug サブディレクトリに含まれます。 マネージ コード (CLR DLL) の場合、このファイルは \WINDEBUG サブディレクトリに含まれます。  
  
## <a name="see-also"></a>参照  
 [多次元モデルのアセンブリの管理](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [ストアド プロシージャの定義](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
