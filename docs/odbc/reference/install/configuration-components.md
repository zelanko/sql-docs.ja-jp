---
title: コンポーネントの構成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], configuring
ms.assetid: 0b68ff48-12e4-41aa-b9e2-b39ed5023ea7
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9c15accf395a33a1af42fe65a3c15612402e381d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="configuration-components"></a>構成コンポーネント
> [!NOTE]  
>  Windows XP および Windows Server 2003 以降、Windows オペレーティング システムに ODBC が含まれます。 以前のバージョンの Windows で ODBC を明示的にのみインストールしてください。  
  
 データ ソースに必要に応じて Dll とトランスレーター セットアップ Dll のセットアップを有効にする呼び出しのドライバーのインストーラーの DLL で構成されます。 DLL は、コントロール パネルから直接呼び出されるか、読み込まれと呼ばれる別のプログラムによって呼び出されますインストーラー、*管理プログラム*です。 次の図は、構成コンポーネント間の関係を示します。  
  
 ![構成コンポーネント間の関係](../../../odbc/reference/install/media/pr30.gif "pr30")  
  
 これらのコンポーネントに関する詳細については、このセクションの最後に、次のトピックを参照してください。  
  
-   [セットアップ プログラム](../../../odbc/reference/install/setup-program.md)  
  
-   [インストーラー DLL](../../../odbc/reference/install/installer-dll.md)  
  
-   [ドライバーのセットアップ DLL](../../../odbc/reference/install/driver-setup-dll.md)  
  
## <a name="see-also"></a>参照  
 [インストール コンポーネント](../../../odbc/reference/install/installation-components.md)
