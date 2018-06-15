---
title: トランスレーター セットアップ Dll |Microsoft ドキュメント
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
- translator setup DLL [ODBC]
ms.assetid: b3ca79e9-01b9-4541-81de-bbbad24ca736
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 65eca03533940a50a169a948021342f71a032153
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915647"
---
# <a name="translator-setup-dlls"></a>トランスレーター セットアップ Dll
> [!NOTE]  
>  Windows XP および Windows Server 2003 以降、Windows オペレーティング システムに ODBC が含まれます。 以前のバージョンの Windows で ODBC を明示的にのみインストールしてください。  
  
 DLL を含む変換プログラムのセットアップ、 **ConfigTranslator**関数で、変換プログラムの既定のオプションを返します。 必要に応じて、ユーザーにこの情報メッセージが表示されます。 この関数の詳細については、次を参照してください。[セットアップ DLL の API リファレンス](../../../odbc/reference/syntax/setup-dll-api-reference.md)です。  
  
 トランスレーター セットアップ DLL は、変換プログラムの開発者によって書き込まれます。 変換プログラムの一部にすることができます、または別の DLL。
