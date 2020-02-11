---
title: SQL Server Compact Edition 接続マネージャーエディター ([すべて] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlmobileconnection.all.f1
helpviewer_keywords:
- SQL Server Compact Connection Manager Editor
ms.assetid: f9fbff4b-c502-44b3-8e7b-398d66e82206
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8a26587f9dd426cdf53a3a53a36d0e81e95ebf77
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66055469"
---
# <a name="sql-server-compact-edition-connection-manager-editor-all-page"></a>[SQL Server Compact Edition 接続マネージャー エディター] ([すべて] ページ)
  
  **[SQL Server Compact Edition 接続マネージャー エディター]** ダイアログ ボックスでは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact データベースに接続するためのプロパティを指定できます。  
  
 
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact Edition 接続マネージャーについて詳しくは、「 [SQL Server Compact Edition 接続マネージャー](connection-manager/sql-server-compact-edition-connection-manager.md)」をご覧ください。  
  
## <a name="options"></a>オプション  
 **自動圧縮のしきい値**  
 
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact データベース ファイルの空き容量 (%) がどの程度になったら自動圧縮プロセスを実行するかを指定します。  
  
 **既定のロックのエスカレーション**  
 
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact データベースが、ロックのエスカレートを試行する前に取得するデータベース ロックの数を指定します。  
  
 **既定のロックタイムアウト**  
 トランザクションがロックを待機する既定の間隔を、ミリ秒単位で指定します。  
  
 **フラッシュ間隔**  
 トランザクションがコミットされてから、ディスクにフラッシュされるまでの間隔を秒単位で指定します。  
  
 **ロケール識別子**  
 
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact データベースのロケール ID (LCID) を指定します。  
  
 **最大バッファーサイズ**  
 
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact が、データをディスクにフラッシュするまでに使用する最大メモリ容量を KB 単位で指定します。  
  
 **最大データベースサイズ**  
 
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact データベースの最大サイズを MB 単位で指定します。  
  
 **モード**  
 
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact データベースを開くファイル モードを指定します。 このプロパティの既定値は **[Read Write]** です。  
  
 [Mode] オプションには、次の表に示すように 4 つの値が用意されています。  
  
|値|[説明]|  
|-----------|-----------------|  
|**読み取り専用**|データベースに対する読み取り専用アクセスを指定します。|  
|**読み取り/書き込み**|データベースに対する読み取り/書き込み権限を指定します。|  
|**排他的**|データベースに対する排他アクセスを指定します。|  
|**共有読み取り**|他のユーザーがデータベースからの読み取りを同時に行うことができることを指定します。|  
  
 **セキュリティ情報を保持する**  
 セキュリティ情報を接続文字列の一部として返すかどうかを指定します。 このオプションの既定値は **[False]** です。  
  
 **一時ファイルディレクトリ**  
 
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 一時データベース ファイルの場所を指定します。  
  
 **Data Source**  
 
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact データベースの名前を指定します。  
  
 **パスワード**  
 
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact データベースのパスワードを入力します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [SQL Server Compact Edition 接続マネージャーエディター &#40;接続ページ&#41;](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-connection-page.md)  
  
  
