---
title: パッケージのコピーを保存 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.savecopyas.f1
helpviewer_keywords:
- Save Copy of Package dialog box
ms.assetid: 7b44c0d7-d8fa-4491-8836-0899f621d3a8
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b42f6861aadb98d97d1b95f688f9dcb891c01697
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074410"
---
# <a name="save-copy-of-package"></a>[パッケージのコピーの保存]
  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] の **[パッケージのコピーの保存]** ダイアログ ボックスを使用すると、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージのコピーを [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] から別の場所に保存し、必要に応じてパッケージの保護レベルを変更できます。  
  
## <a name="options"></a>および  
 **[パッケージの場所]**  
 パッケージ コピーを保存する格納場所の種類を選択します。 使用できるオプションは以下のとおりです。  
  
 **SQL Server**  
  
 **[ファイル システム]**  
  
 **[SSIS パッケージ ストア]**  
  
 **[サーバー]**  
 サーバー名を入力するか、サーバーを一覧から選択します。 このオプションは、格納場所が **[SQL Server]** または **[SSIS パッケージ ストア]** の場合のみ使用できます。  
  
 **[認証]**  
 Windows 認証または [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を選択します。 このオプションは、格納場所が [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の場合のみ使用できます。  
  
> [!IMPORTANT]  
>  可能であれば、Windows 認証を使用します。  
  
 **認証の種類**  
 認証の種類を選択します。  
  
 **ユーザー名**  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用する場合は、ユーザー名を指定します。  
  
 **Password**  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用する場合は、パスワードを指定します。  
  
 **[パッケージのパス]**  
 パッケージ パスを入力するか、 **[...]** ボタンをクリックしてパッケージを格納するフォルダーを見つけます。  
  
 **保護レベル**  
 **[...]** ボタンを押して、 **[パッケージの保護レベル]** ダイアログ ボックスで保護レベルを更新します。 詳細については、「 [[パッケージの保護レベル] ダイアログ ボックス](../../2014/integration-services/package-and-project-protection-level-dialog-box.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [インポート パッケージ ダイアログ ボックスの UI リファレンス](../../2014/integration-services/import-package-dialog-box-ui-reference.md)   
 [[パッケージ] ダイアログ ボックスの UI リファレンスをエクスポートします。](../../2014/integration-services/export-package-dialog-box-ui-reference.md)   
 [パッケージを保存する](save-packages.md)   
 [パッケージ インポートおよびエクスポート&#40;SSIS サービス&#41;](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  