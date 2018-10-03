---
title: 設定またはパッケージの保護レベルの変更 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- passwords [Integration Services]
- packages [Integration Services],security
- security [Integration Services],protection levels
- protection level for packages [Integration Services]
ms.assetid: 904a5580-82ba-4a26-b0c5-d1c989975f61
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 766a0c03bc47527d27fec6e50f2525284a6bdd0a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48204152"
---
# <a name="set-or-change-the-protection-level-of-packages"></a>パッケージの保護レベルを設定または変更する
  パッケージの内容やパッケージに含まれているパスワードなどの機密データへのアクセスを制御するには、`ProtectionLevel` プロパティの値を設定します。 プロジェクトをビルドするには、プロジェクトに含まれるパッケージの保護レベルがプロジェクトと同じである必要があります。 `ProtectionLevel` プロパティ設定をプロジェクトで変更する場合は、パッケージのプロパティ設定を手動で更新する必要があります。  
  
 確認する方法については、`ProtectionLevel`パッケージに適したさまざまな段階でパッケージのライフ サイクルでは設定を参照してください[パッケージ内の機密データのアクセス制御](security/access-control-for-sensitive-data-in-packages.md)します。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のセキュリティ機能の概要については、「[セキュリティの概要 #40; Integration Services & #41;](security/security-overview-integration-services.md)」を参照してください。  
  
 このトピックの手順では、いずれかを使用する方法をについて説明する[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]または dtutil コマンド プロンプト ユーティリティを変更する、`ProtectionLevel`プロパティ。  
  
> [!NOTE]  
>  このトピックの手順、に加えて通常を設定できますまたは変更、`ProtectionLevel`インポートまたはパッケージをエクスポートするときに、パッケージのプロパティ。 また、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードを使用してパッケージを保存するときにも、パッケージの `ProtectionLevel` プロパティを変更できます。  
  
### <a name="to-set-or-change-the-protection-level-of-a-package-in-sql-server-data-tools"></a>SQL Server データ ツールでパッケージの保護レベルを設定または変更するには  
  
1.  使用できる値を確認、`ProtectionLevel`プロパティのトピック「[パッケージの保護レベルを設定](security/access-control-for-sensitive-data-in-packages.md)しパッケージの適切な値を決定します。  
  
2.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、パッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
3.  [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーでパッケージを開きます。  
  
4.  [プロパティ] ウィンドウにパッケージのプロパティが表示されない場合は、デザイン画面をクリックします。  
  
5.  [プロパティ] ウィンドウでの**セキュリティ**グループで、適切な値を選択、`ProtectionLevel`プロパティ。  
  
     パスワードを必要とする保護レベルを選択する場合は、 **[PackagePassword]** プロパティの値としてパスワードを入力します。  
  
6.  **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックして、変更したパッケージを保存します。  
  
### <a name="to-set-or-change-the-protection-level-of-packages-at-the-command-prompt"></a>コマンド プロンプトでパッケージの保護レベルを設定または変更するには  
  
1.  使用できる値を確認、`ProtectionLevel`プロパティのトピック「[パッケージの保護レベルを設定](security/access-control-for-sensitive-data-in-packages.md)しパッケージの適切な値を決定します。  
  
2.  マッピングを確認、`Encrypt`オプションのトピック「 [dtutil ユーティリティ](dtutil-utility.md)、選択した値として使用する整数を適切な判断と`ProtectionLevel`プロパティ。  
  
3.  コマンド プロンプト ウィンドウを開きます。  
  
4.  コマンド プロンプトでは、パッケージには設定するパッケージが含まれているフォルダーに移動します。、`ProtectionLevel`プロパティ。  
  
     次の手順に示す構文の例では、このフォルダーは現在のフォルダーであると想定しています。  
  
5.  次のいずれかの例のようなコマンドを使用して、パッケージの保護レベルを設定または変更します。  
  
    -   次のコマンド セット、`ProtectionLevel`レベル 2 で暗号化するパスワード"、パスワードが"strongpassword"にファイル システム内の個々 のパッケージのプロパティ。  
  
         `dtutil.exe /file "C:\Package.dtsx" /encrypt file;"C:\Package.dtsx";2;strongpassword`  
  
    -   次のコマンドでは、ファイル システム内の特定のフォルダーに存在するすべてのパッケージの `ProtectionLevel` プロパティがレベル 2 の [機微なデータをパスワードで暗号化する] に設定され、パスワードが "strongpassword" に設定されます。  
  
         `for %f in (*.dtsx) do dtutil.exe /file %f /encrypt file;%f;2;strongpassword`  
  
         バッチ ファイルで同様のコマンドを使用する場合は、ファイルのプレースホルダー「%f」をバッチ ファイルでは「%%f」と入力します。  
  
## <a name="see-also"></a>関連項目  
 [dtutil ユーティリティ](dtutil-utility.md)  
  
  
