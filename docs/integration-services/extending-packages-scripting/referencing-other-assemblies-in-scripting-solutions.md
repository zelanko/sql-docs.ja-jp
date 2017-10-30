---
title: "スクリプト ソリューションの他のアセンブリを参照している |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- SSIS Script task, .NET Framework
- Script task [Integration Services], adding references
- referencing custom assemblies
- SSIS Script task, VisualBasic namespace
- assemblies [Integration Services]
- VisualBasic namespace
- Script task [Integration Services], VisualBasic namespace
- Microsoft.VisualBasic namespace
- Script task [Integration Services], .NET Framework
- .NET Framework [Integration Services]
- referencing Web services
ms.assetid: 9b655bcd-19f6-43d8-9f89-1b4d299c6380
caps.latest.revision: 68
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3deb13c7e3aeb2e974ac6e6582555a617346a298
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="referencing-other-assemblies-in-scripting-solutions"></a>スクリプティング ソリューションでの他のアセンブリの参照
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]クラス ライブラリにカスタム機能を実装するための強力な一連のツールとスクリプトの開発者の提供[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]パッケージです。 スクリプト タスクとスクリプト コンポーネントでは、カスタム マネージ アセンブリも使用できます。  
  
> [!NOTE]  
>  オブジェクトおよび Web サービスからメソッドを使用する、パッケージを有効にするを使用して、 **Web 参照の追加**コマンドで使用できる[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA)。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の以前のバージョンでは、Web サービスを使用するためにプロキシ クラスを生成する必要がありました。  
  
## <a name="using-a-managed-assembly"></a>マネージ アセンブリの使用  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]デザイン時にマネージ アセンブリを検索するには、次の手順を行う必要があります。  
  
1.  マネージ アセンブリをコンピューター上の任意のフォルダーに格納します。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の以前のバージョンで追加できたのは、%windir%\Microsoft.NET\Framework\vx.x.xxxxx フォルダーか %ProgramFiles%\Microsoft SQL Server\100\SDK\Assemblies フォルダーにあるマネージ アセンブリへの参照のみでした。  
  
2.  マネージ アセンブリへの参照を追加します。  
  
     VSTA での参照を追加する、**参照の追加**ダイアログ ボックスの**参照** タブを特定し、マネージ アセンブリを追加します。  
  
 実行時に [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によってマネージ アセンブリが検出されるようにするには、次の手順を実行する必要があります。  
  
1.  マネージ アセンブリに厳密な名前で署名します。  
  
2.  パッケージが実行されるコンピューターのグローバル アセンブリ キャッシュに、そのアセンブリをインストールします。  
  
     詳細については、次を参照してください。[構築, Deploying, and Debugging Custom Objects](../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)です。  
  
## <a name="using-the-microsoft-net-framework-class-library"></a>Microsoft .NET Framework クラス ライブラリの使用  
 スクリプト タスクおよびスクリプト コンポーネントは、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] クラス ライブラリによって公開されている他のすべてのオブジェクトおよび機能を利用することができます。 たとえば、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] を使用すると、ユーザーの環境に関する情報を取得し、パッケージを実行中のコンピューターとやり取りできます。  
  
 使用頻度の高い [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] クラスを次に示します。  
  
-   **System.Data** ADO.NET のアーキテクチャが含まれています。  
  
-   **System.IO**ストリーム、ファイル システムへのインターフェイスを提供します。  
  
-   **System.Windows.Forms**フォームの作成を提供します。  
  
-   **System.Text.RegularExpressions**正規表現を操作するためのクラスを提供します。  
  
-   **System.Environment**ローカル コンピューターでは、現在のユーザーおよびコンピューターとユーザーの設定に関する情報を返します。  
  
-   **System.Net**ネットワーク通信を提供します。  
  
-   **System.DirectoryServices** Active Directory を公開します。  
  
-   **System.Drawing**広範な画像操作ライブラリを提供します。  
  
-   **System.Threading**マルチ スレッド プログラミングを有効にします。  
  
 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] の詳細については、MSDN ライブラリを参照してください。  
  
## <a name="see-also"></a>参照  
 [スクリプトによるパッケージの拡張](../../integration-services/extending-packages-scripting/extending-packages-with-scripting.md)  
  
  

