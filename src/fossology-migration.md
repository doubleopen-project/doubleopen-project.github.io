# Migrate Fossology database

The Fossology database cane be migrated from an instance to another. This can be useful if the
pipeline needs to be executed without access to the public Fossology instance.

## Create archive from the existing database volume

1. Get the database volume from existing Fossology instance and create an archive from the volume.
   The volume is expected to be named `fossology_database`.

   ```console
   docker run --rm \
     --volume fossology_database:/dbdata:ro \
     --volume $PWD:/backup \
     ubuntu tar czvf /backup/DATE.tar.gz /dbdata
   ```

## Create a named Docker volume from the archived database

1. Create a temporary container with a named volume.

   ```console
   docker create \
     --volume fossy_migration:/dbdata \
     --name fossy_migration \
     busybox true
   ```

2. Extract the database archive to the created volume.

   ```console
   docker run --rm \
     --volumes-from fossy_migration \
     --volume $PWD:/backup:ro \
     ubuntu bash \
     -c "cd /dbdata && tar xvf /backup/DATE_database --strip 1"
   ```

## Launch Fossology

1. Clone Fossology from <https://github.com/fossology/fossology/>.
2. `git checkout 19d85bd77e0004206caf69a185377a65787543ec` (currently used version, might work with
   later versions as well).
3. Change Docker to use the created volume by changing the volume `database` in
   `docker-compose.yml` to use an external volume with the given name:

   ```yaml
   volumes:
     database:
       external: true
       name: fossy_migration
   ```

4. Launch Fossology with `docker-compose up -d`.
