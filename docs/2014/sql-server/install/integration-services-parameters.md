---
title: Integration Services Parameters |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, parameters
ms.assetid: b1bb3ea3-8097-4e76-b9c2-78a0f46a23bc
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 100e796bb27d1e60db000a364a0432273dd5cafb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66094242"
---
# <a name="integration-services-parameters"></a>Integration Services パラメーター
  では、コンピューター上のパッケージ[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]を分析するか、ファイル[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]システム内のパッケージファイルを分析するかを決定できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ファイル システムのファイルを分析する場合は、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを含むフォルダーのパスを指定します。  
  
## <a name="options"></a>オプション  
 **[コンピューターの SSIS パッケージを分析する]**  
 コンピューター上の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを分析するときは、このオプションを選択します。 既定では、このオプションが選択されています。  
  
 **[SSIS パッケージ ファイルを分析する]**  
 ファイル システムの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを分析するときは、このオプションを選択します。  
  
 **[SSIS パッケージのパス]**  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージが保存されている UNC またはローカル パスを指定します。 ファイル名を含める必要はありません。 入力したパスにアクセスできない場合は、[**次へ**] をクリックすることはできません。 既定では、パスは空白です。 このフィールドは、[ **SSIS パッケージファイルの分析**] を選択した場合にのみ有効になります。  
  
## <a name="see-also"></a>参照  
 [アップグレードアドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [アップグレード アドバイザーのユーザー インターフェイス リファレンス](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
