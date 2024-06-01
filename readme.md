Test został skonfigurowany pod sprawdzenie zagrożeń poziomu high i critical. 
W przypadku znalezienia zagrożenia workflow zostanie zatrzymany
W poniższym fragmencie kodu przedstawione jest użycie docker scout sprawdzajace te zagrozenia:
```
      - 
        name: Docker Scout
        id: docker-scout
        if: ${{ github.event_name == 'pull_request' }}
        uses: docker/scout-action@v1
        with:
          command: cves
          image: ${{ steps.meta.outputs.tags }}
          only-severities: critical,high
          exit-code: true
```