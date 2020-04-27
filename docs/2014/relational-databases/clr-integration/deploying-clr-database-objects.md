---
title: CLR データベースオブジェクトの配置 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- deployment script [CLR integration]
- common language runtime [SQL Server], deploying
- deploying assemblies [CLR integration]
- deploying [CLR integration]
ms.assetid: 00752573-3367-41a7-af98-7b7a29e8e2f2
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4e06dfced9b9800c0e5c0b7d0dca208bac67c900
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62920842"
---
# <a name="deploying-clr-database-objects"></a>CLR データベース オブジェクトの配置
  配置は、完了したアプリケーションまたはモジュールを別のコンピューターにインストールし、実行するために配布するプロセスです。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio を使用して、共通言語ランタイム (CLR) データベース オブジェクトを開発し、これらをテスト サーバーに配置することができます。 また、Visual Studio ではなく [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework の再配布ファイルを使用して、マネージド データベース オブジェクトをコンパイルすることも可能です。 コンパイルすると、CLR データベース オブジェクトを含むアセンブリを、Visual Studio または [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを使用して、テスト サーバーに配置することができます。 Visual Studio .NET 2003 は、CLR 統合プログラミングまたは配置には使用できない点に注意してください。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] には .NET Framework がプレインストールされていますが、Visual Studio .NET 2003 では .NET Framework 2.0 アセンブリを使用できません。  
  
 CLR メソッドをテスト サーバーでテストおよび検証すると、配置スクリプトを使用してこれらを実稼働サーバーに配布できます。 配置スクリプトは手動で生成するか、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] を使用して生成することができます (後に示す手順を参照)。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、既定で CLR 統合機能は無効になっており、CLR アセンブリを使用するには、これを有効にする必要があります。 詳細については、「 [CLR 統合の有効化](clr-integration-enabling.md)」を参照してください。  
  
## <a name="deploying-the-assembly-to-the-test-server"></a>テスト サーバーへのアセンブリの配置  
 Visual Studio を使用し、CLR 関数、プロシージャ、トリガー、ユーザー定義型 (UDT)、またはユーザー定義集計 (UDA) を開発したり、これらをテスト サーバーに配置することができます。 これらのマネージド データベース オブジェクトは、.NET Framework 再配布ファイルに含まれる csc.exe や vbc.exe などのコマンド ライン コンパイラによりコンパイルすることもできます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のマネージド データベース オブジェクトを開発するのに、Visual Studio 統合開発環境は必要ありません。  
  
 すべてのコンパイラ エラーおよび警告が解決されていることを確認してください。 これで、Visual Studio または [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ステートメントを使用して、CLR ルーチンを含むアセンブリを [!INCLUDE[tsql](../../../includes/tsql-md.md)] データベースに登録できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Visual Studio を使用してリモートで開発およびデバッグを行うには、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] インスタンスで TCP/IP ネットワーク プロトコルを有効にする必要があります。 サーバーで TCP/IP プロトコルを有効にする方法の詳細については、「[クライアントプロトコルを構成する](../../database-engine/configure-windows/configure-client-protocols.md)」を参照してください。  
  
#### <a name="to-deploy-the-assembly-using-visual-studio"></a>Visual Studio を使用してアセンブリを配置するには  
  
1.  **[ビルド] メニュー**の [プロジェクト名の> の**ビルド** \<] を選択して、プロジェクトをビルドします。  
  
2.  アセンブリをテスト サーバーに配置する前に、すべてのビルド エラーおよび警告を解決します。  
  
3.  [**ビルド**] メニューの [**配置**] をクリックします。 これで、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス内および [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] プロジェクトを最初に Visual Studio で作成したときに指定したデータベース内にアセンブリが登録されます。  
  
#### <a name="to-deploy-the-assembly-using-transact-sql"></a>Transact-SQL を使用してアセンブリを配置するには  
  
1.  .NET Framework に含まれるコマンド ライン コンパイラを使用して、ソース ファイルからアセンブリをコンパイルします。  
  
2.  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# ソース ファイルの場合は、次のコマンドを実行します。  
  
3.  `csc /target:library C:\helloworld.cs`  
  
4.  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic ソース ファイルの場合は、次のコマンドを実行します。  
  
 `vbc /target:library C:\helloworld.vb`  
  
 これらのコマンドでは、`/target` オプションを使用してライブラリ DLL をビルドすることを指定し、Visual C# コンパイラまたは Visual Basic コンパイラを起動します。  
  
1.  アセンブリをテスト サーバーに配置する前に、すべてのビルド エラーおよび警告を解決します。  
  
2.  テスト サーバーで [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] を開きます。 適切なテスト データベース (AdventureWorks など) に接続して、新しいクエリを作成します。  
  
3.  次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] をクエリに追加することにより、サーバーにアセンブリを作成します。  
  
 `CREATE ASSEMBLY HelloWorld from 'c:\helloworld.dll' WITH PERMISSION_SET = SAFE;`  
  
1.  次に、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに、プロシージャ、関数、集計、ユーザー定義型、またはトリガーを作成する必要があります。 `HelloWorld` アセンブリに、`HelloWorld` クラスの `Procedures` という名前のメソッドが含まれている場合、次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] をクエリに追加して、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に `hello` というプロシージャを作成することができます。  
  
 `CREATE PROCEDURE hello`  
  
 `AS`  
  
 `EXTERNAL NAME HelloWorld.Procedures.HelloWorld`  
  
 で[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のさまざまな種類の管理されたデータベースオブジェクトの作成の詳細については、「 [Clr ユーザー定義関数](../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)」、「clr[ユーザー定義集計](../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)」、「clr ユーザー定義[型](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)」、「Clr[ストアドプロシージャ](../../database-engine/dev-guide/clr-stored-procedures.md)」、および「 [clr トリガー](../../database-engine/dev-guide/clr-triggers.md)」を参照してください。  
  
## <a name="deploying-the-assembly-to-production-servers"></a>実稼働サーバーへのアセンブリの配置  
 CLR データベース オブジェクトをテスト サーバーでテストおよび検証した後は、実稼働サーバーに配布できます。 マネージデータベースオブジェクトのデバッグの詳細については、「 [CLR データベースオブジェクトのデバッグ](debugging-clr-database-objects.md)」を参照してください。  
  
 マネージド データベース オブジェクトの配置は、通常のデータベース オブジェクト (テーブル、[!INCLUDE[tsql](../../../includes/tsql-md.md)] ルーチンなど) の配置と似ています。 CLR データベース オブジェクトを含むアセンブリは、配置スクリプトを使用して別のサーバーに配置できます。 配置スクリプトは、[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] の "スクリプトの生成" 機能を使用して作成できます。 配置スクリプトは、手動で作成することも、また、"スクリプトの生成" を使用して作成した後に手動で変更することもできます。 配置スクリプトの作成後は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の別のインスタンスでこれを実行し、マネージド データベース オブジェクトを配置することができます。  
  
#### <a name="to-generate-a-deployment-script-using-generate-scripts"></a>"スクリプトの生成" 機能を使用して配置スクリプトを生成するには  
  
1.  [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] を開き、配置するマネージド アセンブリまたはデータベース オブジェクトを登録する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスに接続します。  
  
2.  [**オブジェクトエクスプローラー**で、[ ** \<サーバー名>** および**データベース**] ツリーを展開します。 マネージデータベースオブジェクトが登録されているデータベースを右クリックし、[**タスク**]、[**スクリプトの生成**] の順に選択します。 スクリプト作成ウィザードが開きます。  
  
3.  リストボックスからデータベースを選択し、[**次へ**] をクリックします。  
  
4.  [**スクリプトオプションの選択**] ウィンドウで [**次へ**] をクリックするか、オプションを変更して [**次へ**] をクリックします。  
  
5.  [**オブジェクトの種類の選択**] ペインで、配置するデータベースオブジェクトの種類を選択します。 **[次へ]** をクリックします。  
  
6.  [**オブジェクトの種類の選択**] ペインで選択したオブジェクトの種類ごとに、 **[種類の選択\<** ] ペインが表示され>ます。 このペインでは、指定したデータベースに登録されているデータベース オブジェクトの種類のすべてのインスタンスから、いずれかのオブジェクトを選択できます。 1つまたは複数のオブジェクトを選択し、[**次へ**] をクリックします。  
  
7.  必要なデータベースオブジェクトの種類がすべて選択されると、[**出力オプション**] ウィンドウが表示されます。 [**スクリプトをファイルに**作成] を選択し、スクリプトのファイルパスを指定します。 **[次へ]** を選択します。 選択内容を確認し、[**完了**] をクリックします。 配置スクリプトが指定したファイル パスに保存されます。  
  
## <a name="post-deployment-scripts"></a>配置後スクリプト  
 配置後スクリプトの実行が可能です。  
  
 配置後スクリプトを追加するには、Visual Studio のプロジェクト ディレクトリに postdeployscript.sql というファイルを追加します。 たとえば、**ソリューションエクスプローラー**でプロジェクトを右クリックし、[**既存項目の追加**] を選択します。 ファイルは、Test Scripts フォルダーではなく、プロジェクトのルートに追加してください。  
  
 [配置] をクリックすると、プロジェクトの配置後に、このスクリプトが Visual Studio によって実行されます。  
  
## <a name="see-also"></a>参照  
 [CLR &#40;共通言語ランタイム&#41; 統合のプログラミング概念](common-language-runtime-clr-integration-programming-concepts.md)  
  
  
