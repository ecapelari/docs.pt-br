---
title: Método IHostIoCompletionManager::InitializeHostOverlapped
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.InitializeHostOverlapped
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 023e112aa8273d99efce2e0f2116f95569ac0c3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438962"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a>Método IHostIoCompletionManager::InitializeHostOverlapped
Fornece o host com uma oportunidade para inicializar os dados personalizados para acrescentar a Win32 `OVERLAPPED` estrutura que é usada para solicitações de e/s assíncronas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pvOverlapped`  
 [in] Um ponteiro para o Win32 `OVERLAPPED` estrutura a ser incluído na solicitação de e/s.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`InitializeHostOverlapped` retornou com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada foi atingido.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo. As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Não havia memória suficiente disponível para alocar o recurso solicitado.|  
  
## <a name="remarks"></a>Comentários  
 Use as funções da plataforma Windows o `OVERLAPPED` estrutura para armazenar o estado para solicitações de e/s assíncronas. O CLR chama o `InitializeHostOverlapped` método para fornecer o host a oportunidade de acrescentar dados personalizados para um `OVERLAPPED` instância.  
  
> [!IMPORTANT]
>  Para obter o início do seu bloco de dados personalizados, hosts devem definir o deslocamento para o tamanho do `OVERLAPPED` estrutura (`sizeof(OVERLAPPED)`).  
  
 Um valor de retorno de E_OUTOFMEMORY indica que o host falhou ao inicializar seus dados personalizados. Nesse caso, o CLR relata um erro e falha da chamada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [Método GetHostOverlappedSize](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)  
 [Interface IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
