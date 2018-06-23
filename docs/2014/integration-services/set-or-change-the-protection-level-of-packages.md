---
title: 設定またはパッケージの保護レベルを変更する |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- passwords [Integration Services]
- packages [Integration Services],security
- security [Integration Services],protection levels
- protection level for packages [Integration Services]
ms.assetid: 904a5580-82ba-4a26-b0c5-d1c989975f61
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 695667f3ba50b6cde3d2b9629e7116fecf7c4b16
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175377"
---
# <a name="set-or-change-the-protection-level-of-packages"></a>パッケージの保護レベルを設定または変更する
  パッケージの内容やパッケージに含まれているパスワードなどの機密データへのアクセスを制御するには、`ProtectionLevel` プロパティの値を設定します。 プロジェクトをビルドするには、プロジェクトに含まれるパッケージの保護レベルがプロジェクトと同じである必要があります。 `ProtectionLevel` プロパティ設定をプロジェクトで変更する場合は、パッケージのプロパティ設定を手動で更新する必要があります。  
  
 決定する方法については、`ProtectionLevel`パッケージのライフ サイクルのさまざまな段階でパッケージに適切な設定を参照してください[パッケージ内の機密データのアクセス制御](security/access-control-for-sensitive-data-in-packages.md)です。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のセキュリティ機能の概要については、「[セキュリティの概要 #40; Integration Services & #41;](security/security-overview-integration-services.md)」を参照してください。  
  
 このトピックの手順では、いずれかを使用する方法を説明[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]または dtutil コマンド プロンプト ユーティリティを変更する、`ProtectionLevel`プロパティです。  
  
> [!NOTE]  
>  このトピックの手順、に加えて通常を設定できますまたは変更、`ProtectionLevel`インポートまたはパッケージをエクスポートするときに、パッケージのプロパティです。 また、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードを使用してパッケージを保存するときにも、パッケージの `ProtectionLevel` プロパティを変更できます。  
  
### <a name="to-set-or-change-the-protection-level-of-a-package-in-sql-server-data-tools"></a>SQL Server データ ツールでパッケージの保護レベルを設定または変更するには  
  
1.  使用可能な値を確認、 `ProtectionLevel` 、トピック「プロパティ[パッケージの保護レベルを設定](security/access-control-for-sensitive-data-in-packages.md)、し、パッケージの適切な値を決定します。  
  
2.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、パッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
3.  [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーでパッケージを開きます。  
  
4.  [プロパティ] ウィンドウにパッケージのプロパティが表示されない場合は、デザイン画面をクリックします。  
  
5.  [プロパティ] ウィンドウ内で、**セキュリティ**グループで、適切な値を選択、`ProtectionLevel`プロパティです。  
  
     パスワードを必要とする保護レベルを選択する場合は、 **[PackagePassword]** プロパティの値としてパスワードを入力します。  
  
6.  **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックして、変更したパッケージを保存します。  
  
### <a name="to-set-or-change-the-protection-level-of-packages-at-the-command-prompt"></a>コマンド プロンプトでパッケージの保護レベルを設定または変更するには  
  
1.  使用可能な値を確認、 `ProtectionLevel` 、トピック「プロパティ[パッケージの保護レベルを設定](security/access-control-for-sensitive-data-in-packages.md)、し、パッケージの適切な値を決定します。  
  
2.  マッピングを確認、 `Encrypt` 」でオプション[dtutil ユーティリティ](dtutil-utility.md)、選択した値として使用する適切な整数を決定する、`ProtectionLevel`プロパティです。  
  
3.  コマンド プロンプト ウィンドウを開きます。  
  
4.  コマンド プロンプトでパッケージには設定するパッケージが含まれているフォルダーに移動、`ProtectionLevel`プロパティです。  
  
     次の手順に示す構文の例では、このフォルダーは現在のフォルダーであると想定しています。  
  
5.  次のいずれかの例のようなコマンドを使用して、パッケージの保護レベルを設定または変更します。  
  
    -   次のコマンド セット、`ProtectionLevel`レベル 2、「暗号化パスワードを使用して機密」、パスワードが"strongpassword"にファイル システム内の個々 のパッケージのプロパティ。  
  
         `dtutil.exe /file "C:\Package.dtsx" /encrypt file;"C:\Package.dtsx";2;strongpassword`  
  
    -   次のコマンドでは、ファイル システム内の特定のフォルダーに存在するすべてのパッケージの `ProtectionLevel` プロパティがレベル 2 の [機微なデータをパスワードで暗号化する] に設定され、パスワードが "strongpassword" に設定されます。  
  
         `for %f in (*.dtsx) do dtutil.exe /file %f /encrypt file;%f;2;strongpassword`  
  
         バッチ ファイルで同様のコマンドを使用する場合は、ファイルのプレースホルダー「%f」をバッチ ファイルでは「%%f」と入力します。  
  
## <a name="see-also"></a>参照  
 [dtutil ユーティリティ](dtutil-utility.md)  
  
  