#include <stdio.h>

#include <stdlib.h>

#include <string.h>

// Structure to represent a song node

struct Song {
   
    char title[100];
    
    char artist[100];
    
    struct Song* next;

};

// Function to create a new song node

struct Song* createSong(char* title, char* artist) {

    struct Song* newSong = (struct Song*)malloc(sizeof(struct Song));
    
    strcpy(newSong->title, title);
    
    strcpy(newSong->artist, artist);
    
    newSong->next = NULL;
    
    return newSong;

}

// Function to add a song to the end of the playlist

void addSong(struct Song** head, char* title, char* artist) {

    struct Song* newSong = createSong(title, artist);
    
    if (*head == NULL) {
    
        *head = newSong;
        
        return;
    
    }
    
    struct Song* temp = *head;
    
    while (temp->next != NULL) {
    
        temp = temp->next;
    
    }
    
    temp->next = newSong;

}

// Function to display songs in the playlist

void displayPlaylist(struct Song* head) {

    struct Song* temp = head;
    
    printf("Music Playlist:\n");
    
    while (temp != NULL) {
    
        printf("Title: %s, Artist: %s\n", temp->title, temp->artist);
        
        temp = temp->next;
    
    }

}

int main() {

    struct Song* playlist = NULL;

    addSong(&playlist, "Song One", "Artist A");
    
    addSong(&playlist, "Song Two", "Artist B");
    
    addSong(&playlist, "Song Three", "Artist C");

    displayPlaylist(playlist);

    return 0;

}
