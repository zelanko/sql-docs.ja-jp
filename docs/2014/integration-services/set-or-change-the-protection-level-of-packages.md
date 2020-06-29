---
title: パッケージの保護レベルを設定または変更する |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- passwords [Integration Services]
- packages [Integration Services],security
- security [Integration Services],protection levels
- protection level for packages [Integration Services]
ms.assetid: 904a5580-82ba-4a26-b0c5-d1c989975f61
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ae909a1f7a61c5ae2aa3d6319fd03c54dd70b0e1
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85421829"
---
# <a name="set-or-change-the-protection-level-of-packages"></a>パッケージの保護レベルを設定または変更する
  パッケージの内容やパッケージに含まれているパスワードなどの機密データへのアクセスを制御するには、`ProtectionLevel` プロパティの値を設定します。 プロジェクトをビルドするには、プロジェクトに含まれるパッケージの保護レベルがプロジェクトと同じである必要があります。 `ProtectionLevel` プロパティ設定をプロジェクトで変更する場合は、パッケージのプロパティ設定を手動で更新する必要があります。  
  
 パッケージ `ProtectionLevel` のライフサイクルのさまざまな段階でパッケージに適した設定を確認する方法については、「[パッケージ内の機密データの Access Control](security/access-control-for-sensitive-data-in-packages.md)」を参照してください。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のセキュリティ機能の概要については、「[セキュリティの概要 #40; Integration Services & #41;](security/security-overview-integration-services.md)」を参照してください。  
  
 このトピックの手順では、[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] または dtutil コマンド プロンプト ユーティリティを使用して `ProtectionLevel` プロパティを変更する方法について説明します。  
  
> [!NOTE]  
>  このトピックの手順に加えて、通常、パッケージのインポートまたはエクスポート時にパッケージの `ProtectionLevel` プロパティを設定または変更できます。 また、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードを使用してパッケージを保存するときにも、パッケージの `ProtectionLevel` プロパティを変更できます。  
  
### <a name="to-set-or-change-the-protection-level-of-a-package-in-sql-server-data-tools"></a>SQL Server データ ツールでパッケージの保護レベルを設定または変更するには  
  
1.  トピックのプロパティで使用可能な値を確認 `ProtectionLevel` し、パッケージ[の保護レベルを設定](security/access-control-for-sensitive-data-in-packages.md)して、パッケージの適切な値を決定します。  
  
2.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、パッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
3.  [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーでパッケージを開きます。  
  
4.  [プロパティ] ウィンドウにパッケージのプロパティが表示されない場合は、デザイン画面をクリックします。  
  
5.  プロパティウィンドウの**セキュリティ**グループで、プロパティに適切な値を選択し `ProtectionLevel` ます。  
  
     パスワードを必要とする保護レベルを選択する場合は、 **[PackagePassword]** プロパティの値としてパスワードを入力します。  
  
6.  **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックして、変更したパッケージを保存します。  
  
### <a name="to-set-or-change-the-protection-level-of-packages-at-the-command-prompt"></a>コマンド プロンプトでパッケージの保護レベルを設定または変更するには  
  
1.  トピックのプロパティで使用可能な値を確認 `ProtectionLevel` し、パッケージ[の保護レベルを設定](security/access-control-for-sensitive-data-in-packages.md)して、パッケージの適切な値を決定します。  
  
2.  トピック「dtutil ユーティリティ」のオプションのマッピングを確認 `Encrypt` し、選択したプロパティの値として使用する適切な整数を決定し[dtutil Utility](dtutil-utility.md) `ProtectionLevel` ます。  
  
3.  コマンド プロンプト ウィンドウを開きます。  
  
4.  コマンド プロンプトで、`ProtectionLevel` プロパティを設定するパッケージが格納されているフォルダーに移動します。  
  
     次の手順に示す構文の例では、このフォルダーは現在のフォルダーであると想定しています。  
  
5.  次のいずれかの例のようなコマンドを使用して、パッケージの保護レベルを設定または変更します。  
  
    -   次のコマンドでは、ファイル システム内の個々のパッケージの `ProtectionLevel` プロパティがレベル 2 の [機微なデータをパスワードで暗号化する] に設定され、パスワードが "strongpassword" に設定されます。  
  
         `dtutil.exe /file "C:\Package.dtsx" /encrypt file;"C:\Package.dtsx";2;strongpassword`  
  
    -   次のコマンドでは、ファイル システム内の特定のフォルダーに存在するすべてのパッケージの `ProtectionLevel` プロパティがレベル 2 の [機微なデータをパスワードで暗号化する] に設定され、パスワードが "strongpassword" に設定されます。  
  
         `for %f in (*.dtsx) do dtutil.exe /file %f /encrypt file;%f;2;strongpassword`  
  
         バッチ ファイルで同様のコマンドを使用する場合は、ファイルのプレースホルダー「%f」をバッチ ファイルでは「%%f」と入力します。  
  
## <a name="see-also"></a>関連項目  
 [dtutil ユーティリティ](dtutil-utility.md)  
  
  
