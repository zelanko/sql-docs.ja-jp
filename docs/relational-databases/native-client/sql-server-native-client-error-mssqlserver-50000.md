---
title: MSSQLSERVER_50000 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- 50000 [SQL Server Native Client setup error]
ms.assetid: 5426d87a-d5d9-4984-b211-b07d69e834a2
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c94c6ba66c7b943fa029bc1cb7e303cd946b0c4c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305352"
---
# <a name="sql-server-native-client-error-mssqlserver_50000"></a>SQL Server Native Client エラー MSSQLSERVER_50000
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|製品バージョン|11.0|  
|イベント ID|50000|  
|イベント ソース|SETUP|  
|コンポーネント|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client|  
|シンボル名||  
|メッセージ テキスト|ファイル '%.*ls' の読み取り中にネットワーク エラーが発生しました。|  
  
## <a name="explanation"></a>説明  
 名前が sqlncli.msi から変更された MSI ファイルを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client がインストールされているコンピューターで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client をインストール (または更新) しようとしました。  
  
## <a name="user-action"></a>ユーザーの操作  
 このエラーを解決するには、既存のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client をアンインストールします。 このエラーを防ぐには、sqlncli.msi 以外の名前の MSI ファイルから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client をインストールしないようにします。  
  
## <a name="internal-only"></a>内部使用のみ  
  
