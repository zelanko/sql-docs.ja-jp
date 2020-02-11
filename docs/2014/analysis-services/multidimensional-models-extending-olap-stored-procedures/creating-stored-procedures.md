---
title: ストアドプロシージャの作成 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- registering assemblies
- database assemblies [Analysis Services]
- server assemblies [Analysis Services]
- stored procedures [Analysis Services], creating
- assemblies [Analysis Services]
ms.assetid: a12ff02f-6d0b-4488-9846-3609fc0d0554
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7beb77adf595b055a6c1e4a7543b428a06ce7640
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62703089"
---
# <a name="creating-stored-procedures"></a>ストアド プロシージャの作成
  ストアド プロシージャを使用するには、これを共通言語ランタイム (CLR) クラスまたはコンポーネント オブジェクト モデル (COM) クラスに関連付ける必要があります。 クラスは、サーバーにインストールする必要があります。通常は[!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX®ダイナミックリンクライブラリ (DLL) の形式で、サーバーまたは[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベースにアセンブリとして登録します。  
  
 ストアド プロシージャはサーバーまたはデータベースに登録されています。 サーバーのストアド プロシージャは、どのクエリ コンテキストからでも呼び出すことができます。 データベースのストアド プロシージャは、データベース コンテキストが、ストアド プロシージャが定義されているデータベースの場合にのみアクセスできます。 あるアセンブリの関数が別のアセンブリの関数を呼び出す場合は、両方のアセンブリを同じコンテキスト (サーバーまたはデータベース) に登録する必要があります。 サーバーまたはサーバー上に[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]配置されたデータベースの場合、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用してアセンブリを登録できます。 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトの場合は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] デザイナーを使用してプロジェクトにアセンブリを登録できます。  
  
> [!IMPORTANT]  
>  COM アセンブリにより、セキュリティ上のリスクが生じる可能性があります。 このリスクやその他の考慮事項により、[!INCLUDE[ssASversion10](../../includes/ssasversion10-md.md)] では、COM アセンブリが非推奨とされました。 COM アセンブリは、今後のリリースではサポートされない可能性があります。  
  
## <a name="registering-a-server-assembly"></a>サーバー アセンブリの登録  
 
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のオブジェクト エクスプローラーで、サーバー アセンブリは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスの Assemblies フォルダーに一覧表示されます。 サーバー アセンブリには .NET (CLR) アセンブリと COM ライブラリの両方を含めることができます。  
  
### <a name="to-create-a-server-assembly"></a>サーバー アセンブリを作成するには  
  
1.  オブジェクトエクスプローラーでの[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンスを展開し、[**アセンブリ**] フォルダーを右クリックして、[**新しいアセンブリ**] をクリックします。 [**サーバーアセンブリの登録**] ダイアログボックスが表示されます。  
  
2.  [**種類**: アセンブリの種類を指定します。  
  
    -   マネージド コード (CLR) DLL の場合は、.NET アセンブリを指定します。  
  
    -   ネイティブコード (COM) DLL の場合は、COM DLL を指定します。  
  
3.  [**ファイル名**] に、ストアドプロシージャを含む DLL を指定します。  
  
4.  [**アセンブリ名**] には、アセンブリの名前を指定します。  
  
5.  これが、ストアドプロシージャのデバッグに使用するライブラリのデバッグビルドの場合は、[**デバッグ情報を含める**] チェックボックスをオンにします。 ストアドプロシージャのデバッグの詳細については、「[ストアドプロシージャのデバッグ](debugging-stored-procedures.md)」を参照してください。  
  
6.  [ **OK** ] をクリックしてアセンブリをすぐに登録するか、ダイアログボックスのツールバーで [**スクリプト**] メニューのコマンドをクリックして、登録アクションをクエリウィンドウ、ファイル、またはクリップボードにスクリプト化することができます。  
  
 サーバーアセンブリを登録したら、オブジェクトエクスプローラーでアセンブリを右クリックし、[**プロパティ**] をクリックして構成できます。  
  
## <a name="registering-a-database-assembly-on-the-server"></a>サーバーへのデータベース アセンブリの登録  
 
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のオブジェクト エクスプローラーで、データベース アセンブリは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの Assemblies フォルダーに一覧表示されます。 データベース アセンブリには .NET (CLR) アセンブリと COM ライブラリの両方を含めることができます。  
  
### <a name="to-create-a-database-assembly-on-a-server"></a>サーバーでデータベース アセンブリを作成するには  
  
1.  オブジェクトエクスプローラーでデータベースの[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンスを展開し、[**アセンブリ**] フォルダーを右クリックして、[**新しいアセンブリ**] をクリックします。 [**データベースアセンブリの登録**] ダイアログボックスが表示されます。  
  
2.  [**種類**: アセンブリの種類を指定します。  
  
    -   マネージド コード (CLR) DLL の場合は、.NET アセンブリを指定します。  
  
    -   ネイティブ コード (COM) DLL の場合は、COM DLL を指定します。  
  
3.  [**ファイル名**] に、ストアドプロシージャを含む DLL を指定します。  
  
4.  [**アセンブリ名**] には、アセンブリの名前を指定します。  
  
5.  これが、ストアドプロシージャのデバッグに使用するライブラリのデバッグビルドの場合は、[**デバッグ情報を含める**] チェックボックスをオンにします。 ストアドプロシージャのデバッグの詳細については、「[ストアドプロシージャのデバッグ](debugging-stored-procedures.md)」を参照してください。  
  
6.  [ **OK** ] をクリックしてアセンブリをすぐに登録するか、ダイアログボックスのツールバーで [**スクリプト**] メニューのコマンドをクリックして、登録アクションをクエリウィンドウ、ファイル、またはクリップボードにスクリプト化することができます。  
  
 データベースアセンブリを登録したら、オブジェクトエクスプローラーでアセンブリを右クリックし、[**プロパティ**] をクリックして構成できます。  
  
## <a name="registering-a-database-assembly-in-a-project"></a>プロジェクトへのデータベース アセンブリの登録  
 
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のソリューション エクスプローラーで、データベース アセンブリは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトの Assemblies フォルダーに一覧表示されます。 データベース アセンブリには .NET (CLR) アセンブリと COM ライブラリの両方を含めることができます。  
  
### <a name="to-create-a-database-assembly-in-an-analysis-service-project"></a>Analysis Services プロジェクトにデータベース アセンブリを作成するには  
  
1.  オブジェクトエクスプローラーデータベースの[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンスを展開し、[**アセンブリ**] フォルダーを右クリックして、[**新しいアセンブリ参照**] をクリックします。 [参照の**追加**] ダイアログボックスが表示されます。 [**参照の追加**] ダイアログボックスの [ **.net** ] タブには、既存の .net (CLR) アセンブリの一覧が表示されます。 [**プロジェクト**] タブには、プロジェクトが一覧表示されます。  
  
2.  既存の[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]コンポーネントまたはプロジェクトをクリックし、[**追加**] をクリックしてプロジェクトに追加することができます。 COM DLL への参照を追加するには、[**参照**] タブをクリックしてファイルを検索します。 [**選択されたプロジェクトとコンポーネント**] の一覧には、プロジェクトに追加する各コンポーネントの名前、種類、バージョン、および場所が表示されます。  
  
3.  追加するコンポーネントの選択が完了したら、[ **OK** ] をクリックし[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]てプロジェクトに追加します。  
  
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
 [多次元モデルのアセンブリの管理](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [ストアド プロシージャの定義](defining-stored-procedures.md)  
  
  
