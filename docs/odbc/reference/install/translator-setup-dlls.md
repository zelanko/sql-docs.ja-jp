---
title: トランスレーターセットアップ Dll |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- translator setup DLL [ODBC]
ms.assetid: b3ca79e9-01b9-4541-81de-bbbad24ca736
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 28c354fddb36b9e035361fa4ba03fbde34b7d399
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81296052"
---
# <a name="translator-setup-dlls"></a>トランスレーター セットアップ DLL
> [!NOTE]  
>  Windows XP および windows Server 2003 以降では、ODBC は Windows オペレーティングシステムに含まれています。 ODBC は、以前のバージョンの Windows にのみ明示的にインストールする必要があります。  
  
 Translator セットアップ DLL には、変換プログラムの既定のオプションを返す**configtranslator**関数が含まれています。 必要に応じて、ユーザーにこの情報の入力を求めます。 この関数の詳細については、「 [SETUP DLL API Reference](../../../odbc/reference/syntax/setup-dll-api-reference.md)」を参照してください。  
  
 Translator セットアップ DLL は、translator 開発者によって作成されています。 トランスレーター DLL または別の DLL の一部にすることができます。
