---
title: "ストアド プロシージャの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- registering assemblies
- database assemblies [Analysis Services]
- server assemblies [Analysis Services]
- stored procedures [Analysis Services], creating
- assemblies [Analysis Services]
ms.assetid: a12ff02f-6d0b-4488-9846-3609fc0d0554
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 913b2cbb8fbf93be08b1854051024492e691bdea
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="creating-stored-procedures"></a>ストアド プロシージャの作成
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
ストアド プロシージャを使用するには、これを共通言語ランタイム (CLR) クラスまたはコンポーネント オブジェクト モデル (COM) クラスに関連付ける必要があります。 クラスは、サーバーにインストールする必要があります: 通常の形式で、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX® ダイナミック リンク ライブラリ (DLL) — サーバー上またはアセンブリとして登録されていると、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース。  
  
 ストアド プロシージャはサーバーまたはデータベースに登録されています。 サーバーのストアド プロシージャは、どのクエリ コンテキストからでも呼び出すことができます。 データベースのストアド プロシージャは、データベース コンテキストが、ストアド プロシージャが定義されているデータベースの場合にのみアクセスできます。 あるアセンブリの関数が別のアセンブリの関数を呼び出す場合は、両方のアセンブリを同じコンテキスト (サーバーまたはデータベース) に登録する必要があります。 サーバーまたは、展開済みの[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース サーバーでは、使用することができます[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]アセンブリを登録します。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトの場合は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] デザイナーを使用してプロジェクトにアセンブリを登録できます。  
  
> [!IMPORTANT]  
>  COM アセンブリにより、セキュリティ上のリスクが生じる可能性があります。 このリスクやその他の考慮事項により、 [!INCLUDE[ssASversion10](../../includes/ssasversion10-md.md)]では、COM アセンブリが推奨されていません。 COM アセンブリは、今後のリリースではサポートされない可能性があります。  
  
## <a name="registering-a-server-assembly"></a>サーバー アセンブリの登録  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のオブジェクト エクスプローラーで、サーバー アセンブリは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスの Assemblies フォルダーに一覧表示されます。 サーバー アセンブリには .NET (CLR) アセンブリと COM ライブラリの両方を含めることができます。  
  
### <a name="to-create-a-server-assembly"></a>サーバー アセンブリを作成するには  
  
1.  インスタンスを展開[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]オブジェクト エクスプ ローラーで右クリックし、**アセンブリ**フォルダー、およびクリック**新しいアセンブリ**です。 これが表示されます、**サーバー アセンブリの登録** ダイアログ ボックス。  
  
2.  **型**アセンブリの種類を指定します。  
  
    -   マネージ コード (CLR) DLL の場合は、.NET アセンブリを指定します。  
  
    -   ネイティブ コード (COM) DLL は、COM DLL を指定します。  
  
3.  **ファイル名**、ストアド プロシージャを含む DLL を指定します。  
  
4.  **アセンブリ名**アセンブリの名前を指定します。  
  
5.  ライブラリのデバッグを使用しているストアド プロシージャのデバッグ ビルドの場合は、選択、**デバッグ情報を含める**チェック ボックスをオンします。 ストアド プロシージャのデバッグの詳細については、次を参照してください。[ストアド プロシージャのデバッグ](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/debugging-stored-procedures.md)です。  
  
6.  クリックすることができます**OK**アセンブリを登録する、すぐに、またはダイアログ ボックスのツールバーをクリックすると、コマンド、**スクリプト** メニューの登録操作をクエリ ウィンドウ、ファイル、またはクリップボードのスクリプトを作成します。  
  
 サーバー アセンブリを登録した後は、オブジェクト エクスプ ローラーでアセンブリを右クリックし、をクリックして構成できます**プロパティ**です。  
  
## <a name="registering-a-database-assembly-on-the-server"></a>サーバーへのデータベース アセンブリの登録  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のオブジェクト エクスプローラーで、データベース アセンブリは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの Assemblies フォルダーに一覧表示されます。 データベース アセンブリには .NET (CLR) アセンブリと COM ライブラリの両方を含めることができます。  
  
### <a name="to-create-a-database-assembly-on-a-server"></a>サーバーでデータベース アセンブリを作成するには  
  
1.  インスタンスを展開、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]オブジェクト エクスプ ローラーでデータベースを右クリックし、**アセンブリ**フォルダー、およびクリック**新しいアセンブリ**です。 これが表示されます、**データベース アセンブリの登録** ダイアログ ボックス。  
  
2.  **型**アセンブリの種類を指定します。  
  
    -   マネージ コード (CLR) DLL の場合は、.NET アセンブリを指定します。  
  
    -   ネイティブ コード (COM) DLL の場合は、COM DLL を指定します。  
  
3.  **ファイル名**、ストアド プロシージャを含む DLL を指定します。  
  
4.  **アセンブリ名**アセンブリの名前を指定します。  
  
5.  ライブラリのデバッグを使用しているストアド プロシージャのデバッグ ビルドの場合は、選択、**デバッグ情報を含める**チェック ボックスをオンします。 ストアド プロシージャのデバッグの詳細については、次を参照してください。[ストアド プロシージャのデバッグ](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/debugging-stored-procedures.md)です。  
  
6.  クリックすることができます**OK**アセンブリを登録する、すぐに、またはダイアログ ボックスのツールバーをクリックすると、コマンド、**スクリプト** メニューの登録操作をクエリ ウィンドウ、ファイル、またはクリップボードのスクリプトを作成します。  
  
 データベース アセンブリを登録した後は、オブジェクト エクスプ ローラーでアセンブリを右クリックし、をクリックして構成できます**プロパティ**です。  
  
## <a name="registering-a-database-assembly-in-a-project"></a>プロジェクトへのデータベース アセンブリの登録  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のソリューション エクスプローラーで、データベース アセンブリは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトの Assemblies フォルダーに一覧表示されます。 データベース アセンブリには .NET (CLR) アセンブリと COM ライブラリの両方を含めることができます。  
  
### <a name="to-create-a-database-assembly-in-an-analysis-service-project"></a>Analysis Services プロジェクトにデータベース アセンブリを作成するには  
  
1.  インスタンスを展開、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]オブジェクト エクスプ ローラーでデータベースを右クリックし、**アセンブリ**フォルダー、およびクリック**新しいアセンブリ参照**です。 これが表示されます、**参照の追加** ダイアログ ボックス。 **.NET**のタブ、**参照の追加**ダイアログ ボックスで、既存の .NET (CLR) アセンブリが一覧表示中に、**プロジェクト** タブには、プロジェクトが表示されます。  
  
2.  既存のコンポーネントまたはプロジェクトをクリックしてをクリックして**追加**に追加する、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロジェクト。 COM DLL への参照を追加する をクリックして、**参照**タブ ファイルを検索します。 **選択されたプロジェクトとコンポーネント**名前、種類、バージョン、およびプロジェクトに追加する各コンポーネントの場所 ボックスの一覧を示しています。  
  
3.  追加するコンポーネントの選択が完了したら**OK**に追加する、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロジェクト。  
  
## <a name="script-format-for-an-assembly"></a>アセンブリのスクリプト形式  
 .NET アセンブリの登録は簡単です。 .NET アセンブリは次の形式を使用してバイナリ形式でデータベースに追加されます。  
  
```  
<Create>  
   <ObjectDefinition>  
      <Assembly>  
         <Files>  
            <File>  
               <Name>filename</Name>  
               <Type>filetype</Type>  
               <Data>  
                  <Block>binarydatablock</Block>  
                  <Block>binarydatablock</Block>  
                  ...  
               </Data>  
            </File>  
         </Files>  
         <PermissionSet>PermissionSet</PermissionSet>  
      </Assembly>  
   <ObjectDefinition>  
</Create>  
```  
  
## <a name="see-also"></a>参照  
 [多次元モデルのアセンブリの管理](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [ストアド プロシージャの定義](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
