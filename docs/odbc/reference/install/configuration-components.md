---
title: 構成コンポーネント |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], configuring
ms.assetid: 0b68ff48-12e4-41aa-b9e2-b39ed5023ea7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 37c2518c3b18423c804631780ee4a18bff29d88b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81289013"
---
# <a name="configuration-components"></a>構成コンポーネント
> [!NOTE]  
>  WINDOWS XP および Windows Server 2003 以降では、ODBC が Windows のオペレーション システムに含まれています。 ODBC は、以前のバージョンの Windows にのみ明示的にインストールしてください。  
  
 データ ソースはインストーラー DLL によって構成され、必要に応じてドライバー セットアップ DLL とトランスレータ セットアップ DLL が呼び出されます。 インストーラー DLL は、コントロール パネルから直接呼び出されるか、または*管理プログラム*と呼ばれる別のプログラムによって読み込まれ、呼び出されます。 次の図は、構成コンポーネント間の関係を示しています。  
  
 ![構成コンポーネント間の関係](../../../odbc/reference/install/media/pr30.gif "pr30")  
  
 これらのコンポーネントの詳細については、このセクションの最後にある次のトピックを参照してください。  
  
-   [セットアップ プログラム](../../../odbc/reference/install/setup-program.md)  
  
-   [インストーラー DLL](../../../odbc/reference/install/installer-dll.md)  
  
-   [ドライバーのセットアップ DLL](../../../odbc/reference/install/driver-setup-dll.md)  
  
## <a name="see-also"></a>参照  
 [インストール コンポーネント](../../../odbc/reference/install/installation-components.md)
