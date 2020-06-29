---
title: パッケージのコピーを保存する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.savecopyas.f1
helpviewer_keywords:
- Save Copy of Package dialog box
ms.assetid: 7b44c0d7-d8fa-4491-8836-0899f621d3a8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 91c35defd543ae33ed45903e7888da905812d1fc
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85422449"
---
# <a name="save-copy-of-package"></a>[パッケージのコピーの保存]
  **の** [パッケージのコピーの保存] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]ダイアログ ボックスを使用すると、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージのコピーを [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] から別の場所に保存し、必要に応じてパッケージの保護レベルを変更できます。  
  
## <a name="options"></a>オプション  
 **[パッケージの場所]**  
 パッケージ コピーを保存する格納場所の種類を選択します。 次のオプションを使用できます。  
  
 **SQL Server**  
  
 **ファイル システム**  
  
 **SSIS パッケージストア**  
  
 **[サーバー]**  
 サーバー名を入力するか、サーバーを一覧から選択します。 このオプションは、格納場所が **[SQL Server]** または **[SSIS パッケージ ストア]** の場合のみ使用できます。  
  
 **認証**  
 Windows 認証または [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を選択します。 このオプションは、格納場所が [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の場合のみ使用できます。  
  
> [!IMPORTANT]  
>  可能であれば、Windows 認証を使用します。  
  
 **認証の種類**  
 認証の種類を選択します。  
  
 **ユーザー名**  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用する場合は、ユーザー名を指定します。  
  
 **パスワード**  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用する場合は、パスワードを指定します。  
  
 **パッケージ パス**  
 パッケージのパスを入力するか、参照ボタン **([..** .]) をクリックして、パッケージを保存するフォルダーを指定します。  
  
 **保護レベル**  
 参照ボタン **([..** .]) をクリックし、[パッケージの**保護レベル**] ダイアログボックスで保護レベルを更新します。 詳細については、「 [[パッケージの保護レベル] ダイアログ ボックス](../../2014/integration-services/package-and-project-protection-level-dialog-box.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [[パッケージのインポート] ダイアログボックスの UI リファレンス](../../2014/integration-services/import-package-dialog-box-ui-reference.md)   
 [[パッケージのエクスポート] ダイアログボックスの UI リファレンス](../../2014/integration-services/export-package-dialog-box-ui-reference.md)   
 [パッケージの保存](save-packages.md)   
 [パッケージをインポートおよびエクスポートする &#40;SSIS サービス&#41;](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  
