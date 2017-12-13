---
title: "ストアド プロシージャのデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
- debugging stored procedures [Analysis Services]
- stored procedures [Analysis Services], debugging
ms.assetid: 34f51b85-02b3-40dd-bf93-375a9e522385
caps.latest.revision: "26"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9e786c2885f12ceba82d3f49526a1f15f42fb8ef
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="debugging-stored-procedures"></a>デバッグ系のストアド プロシージャ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]ストアド プロシージャは、実際には CLR または COM ライブラリ (通常は Dll) (C#) (またはその他の CLR または COM 言語) で記述されています。 このため、ストアド プロシージャのデバッグは、Visual Studio デバッグ環境で他のアプリケーションをデバッグする作業とほとんど同じになります。 Visual Studio 開発環境でのストアド プロシージャのデバッグは、統合されたデバッグ機能を使用します。 これらの機能を使用すると、プロシージャ内のさまざまな場所で停止し、メモリやレジスタの値を調査し、変数を変更し、メッセージ トラフィックを観察し、コードの動作を詳細にわたって確認することができます。  
  
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
  
    4.  **にアタッチ**テキスト ボックスで、適切なプログラムの種類が選択されているかどうかを確認します。 CLR dll の場合は、**選択**、順にクリックして**コードの種類をデバッグ**、をクリックして**マネージ**、をクリックして**[ok]**です。 COM dll の場合は、**選択**、順にクリックして**コードの種類をデバッグ**、をクリックして**ネイティブ**、をクリックして**[ok]**です。  
  
    5.  をクリックして**アタッチ**です。  
  
7.  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で、ストアド プロシージャを呼び出すプログラムまたは MDX スクリプトを起動します。 デバッガーは、ブレークポイントを含む行に達すると停止します。 ウォッチ ウィンドウで変数を評価し、ロケールを表示し、コードをステップ実行できます。  
  
 ライブラリを正しくデバッグできない場合は、対応するプログラム データベース (PDB) ファイルがサーバーの配置場所にコピーされていることを確認してください。 このファイルが登録または配置中にコピーされなかった場合には、DLL と同じ場所に手動でコピーする必要があります。 ネイティブ コード (COM DLL) の場合、PDB ファイルは \debug サブディレクトリに含まれます。 マネージ コード (CLR DLL) の場合、このファイルは \WINDEBUG サブディレクトリに含まれます。  
  
## <a name="see-also"></a>参照  
 [多次元モデルのアセンブリの管理](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [ストアド プロシージャの定義](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
