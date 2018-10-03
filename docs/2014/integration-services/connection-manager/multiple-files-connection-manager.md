---
title: 複数ファイル接続マネージャー | Microsoft Docs
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
- Multiple Files connection manager
- connection managers [Integration Services], Multiple Files
- connections [Integration Services], files
- multiple file connections
ms.assetid: 10bdc56e-c5cd-4ddb-b2f7-375fe57fe8b2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a0b08bcbf989f2c6fc0bc5b6cc163150b388d797
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48085952"
---
# <a name="multiple-files-connection-manager"></a>複数ファイル接続マネージャー
  複数ファイル接続マネージャーを使用すると、パッケージで既存のファイルやフォルダーを参照したり、実行時にファイルやフォルダーを作成したりできます。  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の組み込みタスクとデータ フロー コンポーネントは、複数ファイル接続マネージャーを使用しません。 ただし、スクリプト タスクまたはスクリプト コンポーネントでは、この接続マネージャーを使用できます。 スクリプト タスクで接続マネージャーを使用する方法については、「 [スクリプト タスクでのデータ ソースへの接続](../extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)」を参照してください。 スクリプト コンポーネントで接続マネージャーを使用する方法については、[スクリプト コンポーネントでのデータ ソースへの接続] を参照してください (../extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md です。  
  
## <a name="usage-types-of-the-multiple-files-connection-manager"></a>複数ファイル接続マネージャーの使用方法の種類  
 複数ファイル接続マネージャーの `FileUsageType` プロパティでは、接続の使用方法を指定します。 複数ファイル接続マネージャーでは、ファイルの作成、フォルダーの作成、既存のファイルの使用、および既存のフォルダーの使用を行うことができます。  
  
 次の表の値`FileUsageType`します。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|複数ファイル接続マネージャーは、既存のファイルを使用します。|  
|**1**|複数ファイル接続マネージャーは、ファイルを作成します。|  
|**2**|複数ファイル接続マネージャーは、既存のフォルダーを使用します。|  
|**3**|複数ファイル接続マネージャーは、フォルダーを作成します。|  
  
## <a name="configuration-of-the-multiple-files-connection-manager"></a>複数ファイル接続マネージャーの構成  
 複数ファイル接続マネージャーをパッケージに追加するときは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって、実行時に複数ファイルの接続を解決する接続マネージャーを作成し、複数ファイルの接続プロパティを設定して、複数ファイルの接続をパッケージの `Connections` コレクションに追加します。  
  
 `ConnectionManagerType`接続マネージャーのプロパティに設定されて`MULTIFILE`します。  
  
 複数ファイル接続マネージャーは、次の方法で構成できます。  
  
-   ファイルとフォルダーの、使用法の種類を指定します。  
  
-   ファイルとフォルダーを指定します。  
  
-   複数のファイルまたはフォルダーを使用する場合、ファイルとフォルダーのアクセス順序を指定します。  
  
 複数ファイル接続マネージャーが複数のファイルとフォルダーを参照する場合、そのファイルとフォルダーのパスは、パイプ (|) 文字で区切ります。 この接続マネージャーの `ConnectionString` プロパティの形式は、次のとおりです。  
  
 \<*パス*>|\<*パス*>  
  
 複数のファイルまたはフォルダーを指定する場合、ワイルドカード文字を使用することもできます。 たとえば、ドライブ C 上のすべてのテキスト ファイルの値の参照を`ConnectionString`プロパティは、c: に設定することができます\\*.txt します。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「 [[ファイル接続マネージャーの追加] ダイアログ ボックスの UI リファレンス](add-file-connection-manager-dialog-box-ui-reference.md)」を参照してください。  
  
 プログラムによる接続マネージャーの構成方法の詳細については、次を参照してください。<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>と[プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)します。  
  
  
