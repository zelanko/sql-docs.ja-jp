---
title: "[全般] ページの統合の Services デザイナー オプション |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Business_Intelligence_Designers.Data_Transformation_Designers.General
ms.assetid: d695690a-923b-4036-945e-7621e8651deb
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 599665d49b8512ec772ac5ca522cb4e0b7a521ec
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="general-page-of-integration-services-designers-options"></a>[Integration Services デザイナー] の [全般] ページのオプション
  **[オプション]** ダイアログ ボックスの **[Integration Services デザイナー]** ページにある **[全般]** ページを使用すると、パッケージの読み込み、表示、およびアップグレードに関するオプションを指定できます。  
  
 **[全般]** ページを開くには、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で **[ツール]** メニューの **[オプション]**をクリックし、 **[ビジネス インテリジェンス デザイナー]**を展開して **[Integration Services デザイナー]**を選択します。  
  
## <a name="options"></a>[全般]  
 **[パッケージの読み込み時にデジタル署名を確認する]**  
 パッケージの読み込み時に [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] でデジタル署名を確認する場合に選択します。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]かどうか、デジタル署名が存在、有効は、信頼されたソースからのみ確認します。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]パッケージが署名された後、パッケージが変更されたかどうかがチェックされます。  
  
 **BlockedSignatureStates** レジストリ値を設定すると、このレジストリ値が、 **[パッケージの読み込み時にデジタル署名を確認する]** オプションよりも優先されます。 詳細については、「 [レジストリ値を設定して署名ポリシーを実装する](../integration-services/packages/implement-a-signing-policy-by-setting-a-registry-value.md)」をご覧ください。  
  
 詳細については、「 [デジタル署名を使用してパッケージのソースを特定する](../integration-services/security/identify-the-source-of-packages-with-digital-signatures.md)」をご覧ください。  
  
 **[パッケージが署名されていない場合、警告を表示する]**  
 署名されていないパッケージが読み込まれたときに、警告を表示します。  
  
 **[優先順位制約ラベルを表示する]**  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]でパッケージを表示する場合に、優先順位制約でどのラベル ([成功]、[失敗]、または [完了]) を表示するかを選択します。  
  
 **[スクリプト言語]**  
 新しいスクリプト タスクおよびスクリプト コンポーネントの既定のスクリプト言語を選択します。  
  
 **[接続文字列を更新して新しいプロバイダー名を使用する]**  
 開くかアップグレード時に[!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)]の現在のリリースに次のプロバイダーの名前を使用する接続文字列の更新プログラムをパッケージ化[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]:  
  
-   [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] OLE DB プロバイダー  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] パッケージ アップグレード ウィザードは、接続マネージャーに格納されている接続文字列だけを更新します。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] の式言語またはスクリプト タスクのコードによって動的に構築される接続文字列は更新しません。  
  
 **[新しいパッケージ ID の作成]**  
 [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] パッケージをアップグレードするとき、アップグレードされたバージョンのパッケージ用に新しいパッケージ ID を作成します。  
  
## <a name="see-also"></a>参照  
 [セキュリティの概要 &#40; Integration Services &#41; です。](../integration-services/security/security-overview-integration-services.md)   
 [スクリプトによるパッケージの拡張](../integration-services/extending-packages-scripting/extending-packages-with-scripting.md)  
  
  

