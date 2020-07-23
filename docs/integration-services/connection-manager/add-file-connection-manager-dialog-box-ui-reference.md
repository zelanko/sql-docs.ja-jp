---
title: '[ファイル接続マネージャーの追加] ダイアログ ボックスの UI リファレンス | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.fileconnection.f1
helpviewer_keywords:
- Add File Connection Manager
ms.assetid: 9370bfb5-5993-4ad8-a9cd-2de53f320f34
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 226dd6c94787af8c32d17cd7bf923a860645c5ac
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "86921718"
---
# <a name="add-file-connection-manager-dialog-box-ui-reference"></a>[ファイル接続マネージャーの追加] ダイアログ ボックスの UI リファレンス

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  **[ファイル接続マネージャーの追加]** ダイアログ ボックスを使用すると、ファイルまたはフォルダーのグループへの接続を定義できます。  
  
 複数のファイルの接続マネージャーの詳細については、「 [Multiple Files Connection Manager](../../integration-services/connection-manager/multiple-files-connection-manager.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の組み込みタスクとデータ フロー コンポーネントは、複数ファイル接続マネージャーを使用しません。 ただし、スクリプト タスクまたはスクリプト コンポーネントでは、この接続マネージャーを使用できます。  
  
## <a name="options"></a>オプション  
 **[使用法の種類]**  
 複数のファイルの接続マネージャーに使用するファイルの種類を指定します。  
  
|値|説明|  
|-----------|-----------------|  
|**[ファイルの作成]**|接続マネージャーはファイルを作成します。|  
|**[既存のファイル]**|接続マネージャーは既存のファイルを使用します。|  
|**[フォルダーの作成]**|接続マネージャーはフォルダーを作成します。|  
|**[既存のフォルダー]**|接続マネージャーは既存のフォルダーを使用します。|  
  
 **[ファイルまたはフォルダー]**  
 次のボタンを使用して追加したファイルまたはフォルダーを表示します。  
  
 **追加**  
 **[ファイルの選択]** ダイアログ ボックスを使用してファイルを追加するか、 **[フォルダーの参照]** ダイアログ ボックスを使用してフォルダーを追加します。  
  
 **[編集]**  
 ファイルまたはフォルダーを選択し、 **[ファイルの選択]** または **[フォルダーの参照]** ダイアログ ボックスを使用して別のファイルまたはフォルダーで置き換えます。  
  
 **Remove**  
 ファイルまたはフォルダーを選択し、 **[削除]** ボタンを使用して一覧から削除します。  
  
 **矢印ボタン**  
 ファイルまたはフォルダーを選択し、矢印ボタンを使用して上または下に移動して、アクセスのシーケンスを指定します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーとメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)  
  
  
