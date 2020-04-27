---
title: ストアドプロシージャのデバッグ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- debugging stored procedures [Analysis Services]
- stored procedures [Analysis Services], debugging
ms.assetid: 34f51b85-02b3-40dd-bf93-375a9e522385
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 90b72b0e60550b0b6bdf89e0ba39e6089c5d8de2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62727748"
---
# <a name="debugging-stored-procedures"></a>デバッグ系のストアド プロシージャ
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のストアド プロシージャは、実際には C# (あるいは他の CLR または COM 言語) で作成されている CLR または COM ライブラリ (通常は DLL) です。 このため、ストアド プロシージャのデバッグは、Visual Studio デバッグ環境で他のアプリケーションをデバッグする作業とほとんど同じになります。 Visual Studio 開発環境でのストアド プロシージャのデバッグは、統合されたデバッグ機能を使用します。 これらの機能を使用すると、プロシージャ内のさまざまな場所で停止し、メモリやレジスタの値を調査し、変数を変更し、メッセージ トラフィックを観察し、コードの動作を詳細にわたって確認することができます。  
  
### <a name="to-debug-a-stored-procedure"></a>ストアド プロシージャをデバッグするには  
  
1.  DLL の作成に使用したプロジェクトを Visual Studio で開きます。  
  
2.  デバッグするプロシージャに対応するメソッドまたは関数内にブレークポイントを作成します。  
  
3.  Visual Studio を使用して、ストアド プロシージャ DLL のデバッグ ビルドを作成します。  
  
4.  DLL をサーバーに配置します。 DLL をサーバーに配置する方法の詳細については、「[ストアドプロシージャの作成](creating-stored-procedures.md)」を参照してください。  
  
5.  テストするストアド プロシージャを呼び出すアプリケーションが必要です。 このようなアプリケーションを用意していない場合は、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の MDX クエリ エディターを使用して、テストするストアド プロシージャを呼び出す MDX クエリを作成できます。  
  
6.  Visual Studio で、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロセス (Msmdsrv.exe) にアタッチします。  
  
    1.  [**デバッグ**] メニューの [**アタッチ toProcess**] を選択します。  
  
    2.  [**アタッチ toProcess** ] ダイアログボックスで、[**すべてのユーザーのプロセスを表示する**] を選択します。  
  
    3.  [**選択可能なプロセス**] の一覧で、[**処理**] 列の**msmdsrv.exe**をクリックします。 サーバーで [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスが複数実行されている場合は、使用するインスタンスの ID を使用してプロセスを識別する必要があります。  
  
    4.  [**アタッチ先**] テキストボックスに、適切なプログラムの種類が選択されていることを確認します。 CLR DLL の場合は、[**選択**] をクリックし、[**次のコードの種類をデバッグ**] をクリックして、[**マネージ**] をクリックし、[ **OK**] をクリックします。 COM DLL の場合は、[**選択**] をクリックし、[**次のコードの種類をデバッグ**] をクリックし、[**ネイティブ**] をクリックして、[ **OK**] をクリックします。  
  
    5.  **[アタッチ]** をクリックします。  
  
7.  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で、ストアド プロシージャを呼び出すプログラムまたは MDX スクリプトを起動します。 デバッガーは、ブレークポイントを含む行に達すると停止します。 ウォッチ ウィンドウで変数を評価し、ロケールを表示し、コードをステップ実行できます。  
  
 ライブラリを正しくデバッグできない場合は、対応するプログラム データベース (PDB) ファイルがサーバーの配置場所にコピーされていることを確認してください。 このファイルが登録または配置中にコピーされなかった場合には、DLL と同じ場所に手動でコピーする必要があります。 ネイティブ コード (COM DLL) の場合、PDB ファイルは \debug サブディレクトリに含まれます。 マネージド コード (CLR DLL) の場合、このファイルは \WINDEBUG サブディレクトリに含まれます。  
  
## <a name="see-also"></a>参照  
 [多次元モデルのアセンブリの管理](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [ストアド プロシージャの定義](defining-stored-procedures.md)  
  
  
