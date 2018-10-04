---
title: ファイル接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- folders [Integration Services], connections
- files [Integration Services], connections
- files [Integration Services]
- connection managers [Integration Services], File
- connections [Integration Services], files
- File connection manager
ms.assetid: 019078bc-44ee-4975-9169-0f9a89e3f3be
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ea35467bd5b5209a2e625adc081774ef39492439
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48119972"
---
# <a name="file-connection-manager"></a>ファイル接続マネージャー
  ファイル接続マネージャーを使用すると、パッケージで既存のファイルやフォルダーを参照したり、実行時にファイルやフォルダーを作成できます。 たとえば、Excel ファイルを参照できます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の特定のコンポーネントでは、ファイルの情報を使用して作業を実行します。 たとえば、SQL 実行タスクでは、そのタスクで実行する SQL ステートメントが含まれるファイルを参照できます。 他のコンポーネントは、ファイルに対する操作を実行します。 たとえば、ファイル システム タスクは新しい場所にコピーするファイルを参照できます。  
  
## <a name="usage-types-of-the-file-connection-manager"></a>ファイル接続マネージャーの使用法の種類  
 `FileUsageType`ファイル接続マネージャーのプロパティは、ファイル接続の使用方法を指定します。 ファイル接続マネージャーでは、ファイルの作成、フォルダーの作成、既存のファイルの使用、または既存のフォルダーの使用を実行できます。  
  
 次の表の値`FileUsageType`します。  
  
|値|説明|  
|-----------|-----------------|  
|`0`|ファイル接続マネージャーは、既存のファイルを使用します。|  
|`1`|ファイル接続マネージャーは、ファイルを作成します。|  
|`2`|ファイル接続マネージャーは、既存のフォルダーを使用します。|  
|`3`|ファイル接続マネージャーは、フォルダーを作成します。|  
  
## <a name="multiple-file-or-folder-connections"></a>複数のファイルまたはフォルダーの接続  
 ファイル接続マネージャーが参照できるファイルまたはフォルダーは、1 つのみです。 複数のファイルまたはフォルダーを参照するには、ファイル接続マネージャーではなく、複数ファイル接続マネージャーを使用します。 詳細については、「 [複数ファイル接続マネージャー](multiple-files-connection-manager.md)」を参照してください。  
  
## <a name="configuration-of-the-file-connection-manager"></a>ファイル接続マネージャーの構成  
 ファイル接続マネージャーをパッケージに追加すると[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]接続マネージャーを実行時にファイルへの接続を解決する、ファイル接続プロパティを設定し、ファイルへの接続を追加します。 作成、`Connections`パッケージのコレクション。  
  
 `ConnectionManagerType`接続マネージャーのプロパティに設定されて`FILE`します。  
  
 ファイル接続マネージャーは、次の方法で構成できます。  
  
-   使用法の種類を指定します。  
  
-   ファイルまたはフォルダーを指定します。  
  
 ファイル接続マネージャーの ConnectionString プロパティは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の [プロパティ] ウィンドウで式を指定することで設定できます。 ただし、式を使用してファイルまたはフォルダーを指定するときの検証エラーを防ぐため、 **[ファイル接続マネージャー エディター]** で、 **[ファイル]/[フォルダー]** に、ファイル パスまたはフォルダー パスを追加してください。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「 [[ファイル接続マネージャー エディター] ダイアログ ボックス](../file-connection-manager-editor.md)」を参照してください。  
  
 プログラムによる接続マネージャーの構成方法の詳細については、次を参照してください。<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>と[プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)します。  
  
  
