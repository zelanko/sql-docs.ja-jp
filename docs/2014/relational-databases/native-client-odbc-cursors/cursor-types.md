---
title: カーソルの種類 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC applications, cursors
- cursors [ODBC], types
- ODBC cursors, types
ms.assetid: 3a916cc7-f352-42cb-8b83-f78e06cef991
author: rothja
ms.author: jroth
ms.openlocfilehash: 6937dbb9ce42cd5631201e0c97be42b211742ada
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85020957"
---
# <a name="cursor-types"></a>カーソルの種類
  ODBC では、Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と Native CLIENT ODBC ドライバーでサポートされる4種類のカーソルを定義して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] います。 これらのカーソルは、結果セットへの変更や、 **tempdb**のメモリや領域など、使用するリソースに対する変更を検出する機能によって異なります。 カーソルが行への変更を検出できるのは、変更が加えられた行の再フェッチを試みたときだけです。現在フェッチしている行への変更を、データ ソースからカーソルに通知する方法はありません。 カーソルを使用して行われなかった変更を検出する機能は、トランザクション分離レベルによって異なる場合があります。  
  
 次に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でサポートされる 4 種類の ODBC カーソルを示します。  
  
-   順方向専用カーソルではスクロールがサポートされず、カーソルの最初から最後まで行を順番にフェッチする機能だけがサポートされます。  
  
-   静的カーソルは、カーソルを開いたときに**tempdb**に構築されます。 静的カーソルは、常に、カーソルを開いた時点の結果セットを表示します。 データへの変更は反映されません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の静的カーソルは常に読み取り専用です。 静的サーバーカーソルは作業テーブルとして**tempdb**に作成されるので、カーソルの結果セットのサイズは、で許容される最大行サイズを超えることはできません [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
-   キーセット ドリブン カーソルでは、カーソルを開くときに、結果セット内の行のメンバーシップと順序が固定されます。 非キー列の変更は、このカーソルを使用して表示されます。  
  
-   動的カーソルは静的カーソルと対照的です。 動的カーソルでは、結果セット内の行に対するすべての変更が反映されます。 結果セット内の行のデータ値、順序、およびメンバーシップは、フェッチを実行するたびに変化する可能性があります。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;カーソルの使用](using-cursors-odbc.md)  
  
  
