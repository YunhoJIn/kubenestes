# 대쉬보드 생성 및 확인
 - kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.2.0/aio/deploy/recommended.yaml
 - kubectl get all -n kubernetes-dashboard

# 대쉬보드 Web UI 실행 및 확인
  - 해당 CMD 창을 이용하기 위해 &를 붙여 BackGrond에서 실행
    - kubectl proxy &
  - 실행확인
    - ps -ef

# 대쉬보드 접속
  - http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/
  - admin 계정 생성
    - kubectl create -f admin_user.yaml
  - admin Token 발행
  - kubectl -n kubernetes-dashboard get secret $(kubectl -n kubernetes-dashboard get sa/admin-user -o jsonpath="{.secrets[0].name}") -o go-template="{{.data.token | base64decode}}"
